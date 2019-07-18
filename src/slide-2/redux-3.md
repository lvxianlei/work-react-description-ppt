## redux-saga 管理和处理异步请求

```
import { all } from 'redux-saga/effects';
import LoginSaga from './Login/saga';
import MainSaga from './Main/saga';
import ListSaga from './List/saga';

export default function* rootSaga() {
    yield all([
        LoginSaga(),
        MainSaga(),
        ListSaga()
    ]);
}
```
