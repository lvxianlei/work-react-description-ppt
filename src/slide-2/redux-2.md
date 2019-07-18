## redux与react-router的连接
```
const PrivateRoute = ({ component: Component, ...rest }) => {
    return (<Route
        {...rest}
        render={props => getItem('access_token') ? (<Component {...props} />) : (<Redirect to={{ pathname: "/" }} />)}
    />);
};

export default (props) => {
    return (
        <Provider store={props.store}>
            <Router history={props.history}>
                <Switch>
                    <Route exact path="/" component={Login} />
                    <PrivateRoute path="/home" component={Main} />
                    <Route component={NoMatch} />
                </Switch>
            </Router>
        </Provider>
    )
};
```