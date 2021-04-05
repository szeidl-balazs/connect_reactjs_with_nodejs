# connect_reactjs_with_nodejs

How To Connect React JS With Node JS
https://www.youtube.com/watch?v=fnpmR6Q5lEc
1. install nodeJS
2. open code editor Visual Studio Code
3. navigate to the project folder
4. npx create-react-app mappa név, npx install and execute packages and app
5. open the project folder
5. a client mappába menni és npm start
6. a fő projekt mappába telepíteni: npx express-generator api
7. Az api mappában npm install
8. terminate the app in client folder int he terminal
9. Az api mappában npm start
10. refresh browser
 
11. bin folder: www
12. change the port number from 3000 to 9000
 
13. Go to routes folder and create new file: testAPI.js
14. in the testAPI.js
var express = require("express");
var router = express.Router();

router.get("/", function(req, res, next) {
	res.send("API is working properly");
});

module.exports = router;

15. in the api folder app.js file
 
app.use("/testAPI", testAPIRouter);

16. in the api folder app.js file
 
testAPIRouter = require("./routes/testAPI");

17.  in the browser: http://localhost:9000/testAPI

18. go to client app, app.js file és lecserélni erre:
class App extends React.Component {
  constructor(props){
    super(props);
    this.state={apiResponse:""}
  }
  callAPI(){
    fetch("http://localhost:9000/testAPI")
    .then(res => res.text())
    .then(res => this.setState({apiResponse: res}));
  }

  componentWillMount(){
    this.callAPI();
  }

  render(){
      return (
      <div className="App">
        <header className="App-header">
          <img src={logo} className="App-logo" alt="logo" />
        </header>
        <p>{this.state.apiResponse}</p>
      </div>
    );
  }
}

export default App;



19. terminate the app in api folder and: npm install --save cors
20. az api/app.js fileban
 

app.use(cors());

21. az api/app.js fileban
 
var cors = require('cors');
