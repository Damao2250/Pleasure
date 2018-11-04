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