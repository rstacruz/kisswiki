- http://stackoverflow.com/questions/34700062/intellij-plugin-airbnb-eslint-w-react/36006123#36006123

## Presets

- https://github.com/airbnb/javascript/blob/master/linters/.eslintrc
- https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb
- https://sqren.github.io/eslint-compare/

Shareable configs are simply npm packages that export a configuration object. To start, create a Node.js module like you normally would. Make sure the module name begins with eslint-config-, such as eslint-config-myconfig. Create a new index.js file and export an object containing your settings.

You can also omit the eslint-config- and it will be automatically assumed by ESLint.

http://eslint.org/docs/developer-guide/shareable-configs

Disable rules from preset:

```
{
  'extends': 'airbnb',
  'rules': {
    'indent': [2, 'tab', { 'SwitchCase': 1, 'VariableDeclarator': 1 }],
    'react/prop-types': 0,
    'react/jsx-indent-props': [2, 'tab'],
  }
}
```

http://stackoverflow.com/questions/27732209/turning-off-eslint-rule-for-a-specific-line

## Ignore

ESLint ignores node_modules by default https://github.com/eslint/eslint/issues/3788#issuecomment-140232261

https://github.com/eslint/eslint/blob/master/.eslintignore

http://stackoverflow.com/questions/32184532/eslintignore-not-working-in-sibling-directory

## fix indent

Looks like indent's auto-fix only knows how to remove or add indent characters. It doesn't seem to detect that, for example, if tabs are expected but a file has spaces, then the whole space range should be replaced with the whole expected tab range. https://github.com/eslint/eslint/issues/4274

## React

http://stackoverflow.com/questions/30294870/how-to-config-eslint-for-react-on-atom-editor

## require.resolve

By default eslint always resolves files in extends relative to the top-level project. Using require.resolve converts the references to absolute paths.

https://github.com/airbnb/javascript/pull/582

https://github.com/groupon/javascript/blob/master/linters/eslint-config-groupon/legacy.js#L28-L48
// ESLint will resolve all references relative to the app,
// not relative to our package.
// We use require.resolve to get absolute paths which will
// always point to the right place.
require.resolve('eslint-config-airbnb/legacy'),

# undef

http://stackoverflow.com/questions/30398825/eslint-window-is-not-defined-how-to-allow-global-variables-in-package-json

## backticks and single quotes not supported both

- https://github.com/eslint/eslint/issues/2153
- https://github.com/eslint/eslint/issues/5234

## eslint and jsx: 'hJSX' is defined but never used

`npm i -D eslint-plugin-react`

.eslintrc

```
{
  'rules': {
    'react/jsx-uses-react': [2, {'pragma': 'hJSX'}],
  },
  'plugins': [
    'react'
  ],
}
```

https://github.com/killercup/cycle-webpack-starter/blob/master/.eslintrc

## const must be uppercase for some cases

Usages (top 4 have to uppercase):

```
const FOO = 'bar';
const FOO = 42;
const FOO = ['bar', 42];
const FOO = {bar: 42, baz: 'qux'};

const foo = `42 ${bar}`;
const foo = bar();
const foo = bar ? baz : 42;
const foo = bar.baz();
const foo = bar => baz;
const foo = {bar: baz};
const foo = [bar, baz, 42];
```

Also this errors:

`const WEEK_IN_MS = 1000 * 60 * 60 * 24 * 7;`

so can be changed to:

`const WEEK_IN_MS = 1000 * 60 * 60 * 24 * 7; // eslint-disable-line`

- https://github.com/k03mad/eslint-plugin-const-case

## git hook

`git-hooks/pre-commit`:

```bash
#!/usr/bin/env bash
frontendFiles=$(git diff --cached --name-only | grep 'frontend/src/.*\.js')
backendFiles=$(git diff --cached --name-only | grep 'backend/app/.*\.js')

if [[ $frontendFiles = "" && $backendFiles = "" ]] ; then
 exit 0
fi

echo "Running eslint..."

result=0

for file in ${frontendFiles}; do
 out=`./frontend/node_modules/.bin/eslint $file`
 if [[ $out != "" ]] ; then
 result=1
 echo "$out"
 fi
done;

for file in ${backendFiles}; do
 out=`./backend/node_modules/.bin/eslint $file`
 if [[ $out != "" ]] ; then
 result=1
 echo "$out"
 fi
done;

if [[ $result != 0 ]] ; then
 echo "ESLint check failed, commit denied"
 exit $result
fi
```

## run recursively

`eslint . --ext .js --ext .jsx`

`eslint './**/*.js'`

http://tips.tutorialhorizon.com/2017/05/04/how-to-run-eslint-recursively-on-all-the-files-in-root-directory-without-glob-patterns/

`eslint './src/**/*.js' './specs/**/*.js'`

https://github.com/eslint/eslint/issues/1663#issuecomment-240066799

## disable partial in jsx

```jsx
    {/* eslint-disable camelcase */}
    <input type="text" placeholder="ADDRESS OF RESIDENCE" name="address_line1" value={address_line1} onChange={onChange} />
    <input type="text" placeholder="ADDRESS LINE 2" name="address_line2" value={address_line2} onChange={onChange} />
    <input type="text" placeholder="CITY" name="address_city" value={address_city} onChange={onChange} />
    <input type="text" placeholder="STATE" name="address_state" value={address_state} onChange={onChange} />
    {/* eslint-enable camelcase */}
```

https://github.com/eslint/eslint/issues/7030

## document is not defined

in `.eslintrc`:

```
{
  "globals": {
    "document": true,
    "foo": true,
    "window": true
  }
}
```

https://stackoverflow.com/questions/30398825/eslint-window-is-not-defined-how-to-allow-global-variables-in-package-json/39331966#39331966
