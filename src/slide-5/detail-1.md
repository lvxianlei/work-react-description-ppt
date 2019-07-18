## index.js文件
```
import Page1 from './component/Page1';
import { connect } from 'react-redux';
import { withRouter } from 'react-router-dom';
export default withRouter(connect(state => { return { Page1: state.get('Page1') } })(Page1));
```