1.使用react脚手架快速搭建模板

    npm install -g create-react-app
    create-react-app demo-app
    cd demo-app

2.安装所必须要的包：

    npm install react-router-dom --save-dev

3.一个基本路由示例

    import React from "react";
    import { BrowserRouter as Router, Route, Link } from "react-router-dom";

    const Index = () => <h2>Home</h2>;
    const About = () => <h2>About</h2>;
    const Users = () => <h2>Users</h2>;

    const AppRouter = () => (
    <Router>
        <div>
        <nav>
            <ul>
                <li>
                    <Link to="/">Home</Link>
                </li>
                <li>
                    <Link to="/about/">About</Link>
                </li>
                <li>
                    <Link to="/users/">Users</Link>
                </li>
            </ul>
        </nav>

        <Route path="/" exact component={Index} />
        <Route path="/about/" component={About} />
        <Route path="/users/" component={Users} />
        </div>
    </Router>
    );

    export default AppRouter;

4.嵌套路由示例

    import React from "react";
    import { BrowserRouter as Router, Route, Link } from "react-router-dom";

    const App = () => (
    <Router>
    <div>
        <Header />

        <Route exact path="/" component={Home} />
        <Route path="/about" component={About} />
        <Route path="/topics" component={Topics} />
    </div>
    </Router>
    );

    const Home = () => <h2>Home</h2>;
    const About = () => <h2>About</h2>;
    const Topic = ({ match }) => <h3>Requested Param: {match.params.id}</h3>;
    const Topics = ({ match }) => (
    <div>
    <h2>Topics</h2>

    <ul>
        <li>
        <Link to={`${match.url}/components`}>Components</Link>
        </li>
        <li>
        <Link to={`${match.url}/props-v-state`}>Props v. State</Link>
        </li>
    </ul>

    <Route path={`${match.path}/:id`} component={Topic} />
    <Route
        exact
        path={match.path}
        render={() => <h3>Please select a topic.</h3>}
    />
    </div>
    );
    const Header = () => (
    <ul>
        <li>
            <Link to="/">Home</Link>
        </li>
        <li>
            <Link to="/about">About</Link>
        </li>
        <li>
            <Link to="/topics">Topics</Link>
        </li>
    </ul>
    );

    export default App;

5.重定向路由

    import React from "react";
    import {
    BrowserRouter as Router,
    Route,
    Link,
    Redirect,
    withRouter
    } from "react-router-dom";

    ////////////////////////////////////////////////////////////
    // 1. Click the public page
    // 2. Click the protected page
    // 3. Log in
    // 4. Click the back button, note the URL each time

    function AuthExample() {
    return (
        <Router>
        <div>
            <AuthButton />
            <ul>
            <li>
                <Link to="/public">Public Page</Link>
            </li>
            <li>
                <Link to="/protected">Protected Page</Link>
            </li>
            </ul>
            <Route path="/public" component={Public} />
            <Route path="/login" component={Login} />
            <PrivateRoute path="/protected" component={Protected} />
        </div>
        </Router>
    );
    }

    const fakeAuth = {
    isAuthenticated: false,
    authenticate(cb) {
        this.isAuthenticated = true;
        setTimeout(cb, 100); // fake async
    },
    signout(cb) {
        this.isAuthenticated = false;
        setTimeout(cb, 100);
    }
    };

    const AuthButton = withRouter(
    ({ history }) =>
        fakeAuth.isAuthenticated ? (
        <p>
            Welcome!{" "}
            <button
            onClick={() => {
                fakeAuth.signout(() => history.push("/"));
            }}
            >
            Sign out
            </button>
        </p>
        ) : (
        <p>You are not logged in.</p>
        )
    );

    function PrivateRoute({ component: Component, ...rest }) {
    return (
        <Route
        {...rest}
        render={props =>
            fakeAuth.isAuthenticated ? (
            <Component {...props} />
            ) : (
            <Redirect
                to={{
                pathname: "/login",
                state: { from: props.location }
                }}
            />
            )
        }
        />
    );
    }

    function Public() {
    return <h3>Public</h3>;
    }

    function Protected() {
    return <h3>Protected</h3>;
    }

    class Login extends React.Component {
    state = { redirectToReferrer: false };

    login = () => {
        fakeAuth.authenticate(() => {
        this.setState({ redirectToReferrer: true });
        });
    };

    render() {
        let { from } = this.props.location.state || { from: { pathname: "/" } };
        let { redirectToReferrer } = this.state;

        if (redirectToReferrer) return <Redirect to={from} />;

        return (
        <div>
            <p>You must log in to view the page at {from.pathname}</p>
            <button onClick={this.login}>Log in</button>
        </div>
        );
    }
    }

    export default AuthExample;