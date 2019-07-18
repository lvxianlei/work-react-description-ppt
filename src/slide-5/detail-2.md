## action.js文件
```
import {
    DELETE_START, DELETE_SUCCESS, DELETE_ERROR,
    SAVEORUPDATE_START, SAVEORUPDATE_SUCCESS, SAVEORUPDATE_ERROR
} from '../../../src/common/API'

export function deleteStart(paload) {
    return {
        type: DELETE_START,
        paload
    }
}

export function deleteSuccess(paload) {
    return {
        type: DELETE_SUCCESS,
        paload
    }
}

export function deleteError(paload) {
    return {
        type: DELETE_ERROR,
        paload
    }
}

```