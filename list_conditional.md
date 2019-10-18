### app.js
```
class App extends Component {
  state = {
    userInput: ''
  }

  inputChangedHandler = (event) => {
    this.setState({userInput: event.target.value});
  }

  deleteCharHandler = (index ) => {
    const text = this.state.userInput.split('');
    text.splice(index, 1);
    const updatedText =   text.join('');
    this.setState({userInput: updatedText});
  }

  render () {
    const charList = this.state.userInput.split('').map((ch, index) => {
      return <Char
              character={ch}
              key={index}
              clicked={() => this.deleteCharHandler(index)}
              />;
    });

    return (
      <div className="App">
        <p>Hint: Keep in mind that JavaScript strings are basically arrays!</p>
        <hr />
        <input
          type="text"
          onChange={this.inputChangedHandler}
          value={this.state.userInput}
        />
        <p>{this.state.userInput}</p>
        <Validation inputLength={this.state.userInput.length}/>
        {charList}
      </div>
    );
  }
}
```

### child component
```
const validation = (props) => {
    let validationMessage = "Text long enough";

    if (props.inputLength <= 5) {
        validationMessage = "Text too short";
    }

    return (
        <div>
            <p>{validationMessage}</p>
        </div>
    );
};
```

```
const char = (props) => {
    const styles = {
        display: 'inline-block',
        padding: '16px',
        margin: '15px',
        border: '1px solid black',
        textAlign: 'center'
    }

    return (
        <div style = {styles} onClick={props.clicked}>
            {props.character}
        </div>
    )
};
```
