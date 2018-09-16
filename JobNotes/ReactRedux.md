# React and its environment learning notes

##React component

ES6 Class

```

Class MyComponent extends React.Component{
    render(){
        return(
            <div>Hello,World!</div>
        );
    }
}

ReactDOM.render(<MyComponent/>,document.getElementById('app));
```

JSX UI design

Virtual DOM

Component PropType & default prop value



MyComponent.propTypes = {
    todo: React.PropTypes.object,
    name: React.PropTypes.string,
}

MyComponent.defaultProps = {
    todo:{},
    name:'',
}

React Component Life Cycle & State

```
const divStyle = {
    color: 'red',
    backgroundImage: 'url(' + imgUrl + ')',
};

ReactDOM.render(<div style={divStyle}>Hello World!</div>, docume
nt.getElementById('app'));
```


JSX

<MessageBox /> vs
```
<form class = "messageBox">
</form>
```

jsx & no jsx

```
React.createElement('a',{href:},'Hello!')
```
Map to generate list

```
const lists = ['a','b'];

class HelloM extends React.Component{
    render(){
        return(
            <ul>
                {lists.map((result,index) =>{
                    return (<li key={index}>{result}</li>);
                })}
            </ul>);
        )
    }
}

```

```
<script type = "text/jsx" src = "main.jsx"></script>
```


JSx uses className and htmlFor property

```
var props = {
    style:"",
    className:"",
    value:"yo",
}

<helloMessage {...props} value = "yo"/>
```

use your own props, use data-





