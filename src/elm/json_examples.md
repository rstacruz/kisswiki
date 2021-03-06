## Decode field to int event if it's string in json

```elm
Decode.map Model
    ("id" := Decode.string |> stringToInt )
```

http://stackoverflow.com/questions/32575003/elm-how-to-decode-data-from-json-api

## optional with pipeline

```
type alias User =
    { age : Maybe Int
    }

user : Decoder User
user =
    decode User
        |> optional "age" (map Just int) Nothing
```

- from dailydrip email
- http://package.elm-lang.org/packages/NoRedInk/elm-decode-pipeline/latest

## mutually recursive decoders

```elm
type Question
    = Question Int (Maybe Answer)


type Answer
    = Answer Int (Maybe Question)


test =
    """{"value":4,"nested":{"value":3,"nested":null}}"""


andMap : Decoder a -> Decoder (a -> b) -> Decoder b
andMap =
    flip (Decode.map2 (<|))


question : Decoder Question
question =
    Decode.succeed Question
        |> andMap (field "value" int)
        |> andMap (field "nested" (nullable (lazy (\_ -> answer))))


answer : Decoder Answer
answer =
    Decode.succeed Answer
        |> andMap (field "value" int)
        |> andMap (field "nested" (nullable (lazy (\_ -> question))))
```

from https://elmlang.slack.com/archives/general/p1483975350012245


## map Nothing

Json.Decode.succeed can be used to wrap a constant value in a decoder:

```elm
type alias Header =
    { value : String
    , term : Maybe String
    }

map2 Header (field "header" string)
    (succeed Nothing)
```

http://stackoverflow.com/questions/41623843/how-to-map-nothing-to-elm-json-decoder

## deeply nested

```elm
redditJsonResponseDecoder : Decoder (List PostContent)
redditJsonResponseDecoder =
    at [ "data", "children" ] <|
        list <|
            at [ "data" ] <|
                object2
                    PostContent
                    ("title" := string)
                    ("permalink" := string)
```

https://www.reddit.com/r/elm/comments/5o5p63/experiences_with_elm_on_a_small_production/

## create a Decoder which only matches a specific string value, and fails with all others

```elm
import Json.Decode.Decoder as Decode exposing (Decoder)

onlyMatchesHello : Decoder ()
onlyMatchesHello =
    let
        checkHello value =
            if value == "hello" then
                Decode.succeed ()
            else
                Decode.fail "Expected \"hello\""
    in
        Decode.string
            |> Decode.andThen checkHello
```

https://groups.google.com/forum/#!msg/elm-discuss/p3lCDdmeAXM/liXIdzzlCwAJ

## maybe list to empty list

I have this:

`maybe (field "users" (list Share.Model.decodeUser))`
 
in my decoder

@ilias:

you have a couple of options:
- json.decode.pipeline has `optionalField`, but if you're not using pipeline, it might be overkill to pull that in
- you could `map (Maybe.withDefault []) <| maybe (field "users" (list Share.Model.decodeUser))`
- you could `oneOf [field "users" (list Share.Model.decodeUser), succeed []]` to say "either successfully run that decoder, or succeed with an empty list"
