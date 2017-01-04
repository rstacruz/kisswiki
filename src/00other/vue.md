> if we had more experienced front-end developers I would probably have pushed for React (and Redux instead of Vuex) as it's not that much harder to learn but takes a bit more experience with Js. One of the main reasons to chose React over Vue is that, It doesn't impose the limitations of a templating engine / directive. For example, as opposed to "v-if render this, v-if render that, v-for render these, etc." you can just use JSX which is like small bits of Javascript controlled Html, and get all the native control structures for free, it is very liberating. Furthermore, you can have your components' description live right besides your business logic instead of in your html.
>
> React will push you to become a better developer by making you think about immutability, among other FP concepts, the ecosystem really is great, solutions for novel problems, as well as best practices and anti-patterns are easy to find, documentation is better (even though Vue's really good, I found some edge cases like deep and immediate watchers buried really deep in the api), and from a management stand point React devs are easier to come around if that's a concern.
>
> I haven't yet worked with Vue (might give 2.0 a try), but from what I've read, you can use JSX with Vue: https://vuejs.org/2016/04/27/announcing-2.0/#Templates-JSX-or-Hyperscript
edit: So you can go both ways. .jsx files with css modules and JSX or vue files with templates and css for your single file components
>
> If your app is getting even slightly more complex you're probably using Redux or any other state handler. They handle it for you. Even if you use local or global state, shouldComponentUpdate makes sense in the rarest of cases, for instance when your data is very abstruse. I have never used it, most people wouldn't, it is an escape hatch for grave case.
>
> The odd thing is that Vues reactivity system can be a mess. It climbs through your data, wildly mutating it, transforming everything into an "observable." Javascript can't observe objects yet, so you run into natural edge cases like not being able to replace or add objects in your data. Then you sprinkle $sets and $deletes over your codebase. Vue even transforms objects that you don't want to be reactive, you hardly have control over what it does. Once behind-the-scene magic has burnt your app to a crisp, you are going to VueX, at which point you are using Redux almost the same way everyone else is using it.
>
> In reality you do have to worry about it because you will run into its edge cases. An "edge case" can be as simple as adding a property to your dataset. Some of this is clearly documented as you say, but that is exactly what is making Vue hard, because it has you study intricate inner workings that affect your app in ways you can't predict. React doesn't do that to you. I haven't read a single React document to this day. I learned it in one or two hours and that was that. I had to study Vue for weeks to truly understand what's going on because in a larger project it goes wild. This is why i said that in the end you'll be with VueX/Redux/MobX anyway.
Here's another example of Vues magic that makes things so easy:
> Sometimes you just want to keep an object inside your component, be it a dom node, a three.js object, whatever. Where do you put it? You can't put it into data because Vue will climb through it and convert hundreds of thousands of objects into observables. You think "hey, let's put it into this.dontTouchThis" - but in certain conditions Vue will still mutate. This for instance is not documented, you'll have to browse through the github issue tracker, see here: https://github.com/vuejs/vue/issues/1988 The solution to it is of course completely arbitrary again, i'm sure you knew that only the "created" hook is guaranteed to not touch your stuff.
> -- https://www.reddit.com/r/javascript/comments/557h8w/thoughts_on_vue_20/

<br>

> templates are limited to the DSL while the programmatic nature of JSX/hyperscript provides the full expressive power of a turing-complete language.
> -- https://vuejs.org/2016/04/27/announcing-2.0/#Templates-JSX-or-Hyperscript