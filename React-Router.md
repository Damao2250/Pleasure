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