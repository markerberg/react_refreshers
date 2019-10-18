# 1
#### main app
```
class App extends Component {
  state = {
    username: 'supermark'
  }

  usernameChangedHandler = (event) => {
    this.setState({username: event.target.value});
  }

  render() {
    return (
      <div className="App">
        <UserInput changed={this.usernameChangedHandler} currentName={this.state.username}/>
        <UserOutput userName={this.state.username}/>
        <UserOutput userName={this.state.username}/>
        <UserOutput userName="mark"/>
      </div>
    );
  }
}
```
#### child components
```
const userOutput = (props) => {
    return (
        <div className="UserOutput">
            <p>Username: {props.userName}</p>
            <p>foo bar</p>
        </div>
    );
};
```
```
const userInput = (props) => {
    const style = {
        border: '2px solid red'
    }

    return <input
        type="text"
        style={style}
        onChange={props.changed}
        value={props.currentName}
    />;
};
```
