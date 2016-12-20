## Decode field to int event if it's string in json

```elm
Decode.map Model
    ("id" := Decode.string |> stringToInt )
```

http://stackoverflow.com/questions/32575003/elm-how-to-decode-data-from-json-api