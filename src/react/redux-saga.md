- pull vs push https://github.com/yelouafi/redux-saga/issues/105#issuecomment-182831804
- http://survivejs.com/blog/redux-saga-interview/
- Saga is a failure management pattern https://medium.com/@roman01la/confusion-about-saga-pattern-bbaac56e622
- alternative http://www.christianalfoni.com/articles/2016_09_11_The-case-for-function-tree
- http://jaysoo.ca/2016/01/03/managing-processes-in-redux-using-sagas/

## flow

dispatch -> take

```
dispatch(signIn(data))

export function signIn (data) {
  return { type: SIGN_IN, data };
}

takeEvery(SIGN_IN, authentication.authenticate, apiService),

```

## takeEvery has been cancelled, uncaught

When some action can throw js error, has to be wrapped with `try .. catch`.
