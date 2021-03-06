## vs flow

> PropTypes can give you warnings during runtime, which can be helpful to quickly find malformed responses coming from a server, etc.
>  babel plugin https://github.com/brigand/babel-plugin-flow-react-proptypes to convert type declarations to PropTypes
> Flow let's you cover more of your codebase, whereas you are limited to props when using PropTypes
> -- http://stackoverflow.com/questions/36065185/react-proptypes-vs-flow

<br>

> we've had many requests to strip out PropTypes from production code since they add significant start up time and file weight for no little use since type checks are disabled.
>
> stripping PropTypes in production https://github.com/oliviertassinari/babel-plugin-transform-react-remove-prop-types
>
> As for using Flow annotations as runtime information (and vice-versa), I've built https://github.com/STRML/json-to-flow to handle converting JSON schemata into Flow types, and @seanhess's runtime-types handles converting Flow types back into JSON.
>
> there's also this for runtime flow checking: https://github.com/gcanti/babel-plugin-tcomb
> -- Replace React.PropTypes with Flow types https://github.com/facebook/flow/issues/277

- https://medium.com/@chenglou/react-proptypes-flow-types-cheat-sheet-ed80f8e1383d
