## 利用redux来管理请求和数据
```
import { createStore, applyMiddleware } from 'redux';
import createSagaMiddleware from 'redux-saga';
import { Provider } from 'react-redux';

const store = { ...createStore(reducers, Map({}), applyMiddleware(sagaMiddleware, routerWare, loggerMiddleware)), runSaga: sagaMiddleware.run };

store.runSaga(rootSaga);

export default store;
```
