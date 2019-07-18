## reducers.js?
#### No 疑惑！，reducer是要合并到一起的。这样才能把数据整合到一起
```
import { combineReducers } from 'redux-immutable';
import { Map } from 'immutable';
import Login from './Login/reducer';
import Main from './Main/reducer';

import { LOCATION_CHANGE } from 'react-router-redux';
const initialState = Map({
    location: null,
    action: null
});

function routerReducer(state = initialState, { type, payload = {} } = {}) {
    if (type === LOCATION_CHANGE) {
        const location = payload.location || payload;
        const action = payload.action;
        return state.set('location', location).set('action', action);
    }
    return state;
}

export default combineReducers({
    routing: routerReducer,
    Login,
    Main
});
```