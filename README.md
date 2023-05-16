# Django-React Todo Backend

This is a simple Django app that provides a RESTful API for a todo list. The app can be used with any front-end framework, such as React.

## Installation
To use the app, simply clone the repository and run the following commands:

```
pip install -r requirements.txt  
python manage.py makemigrations  
python manage.py migrate  
python manage.py runserver  
```

The app will then be available at http://localhost:8000.

## Features
* Create, read, update, and delete todo items.
* Get a list of all todo items.
* Get a list of todo items that are completed.
* Get a list of todo items that are not completed.

## Requirements

* Python 3.6+
* Django 3.2+



### The app can be used with any front-end framework. Here is an example of how to use the app with React:

1. Install React and create a new project:

`npm install -g create-react-app todo-app`

2. Install the axios package:

`npm install axios`

3. Open App.js and add the following code:
```
import React, { Component } from "react";
import axios from "axios";

class App extends Component {
  state = {
    todos: []
  };

  componentDidMount() {
    axios.get("/todos").then(response => {
      this.setState({ todos: response.data });
    });
  }

  addTodo = () => {
    const todo = {
      title: this.input.value
    };

    axios.post("/todos", todo).then(response => {
      this.setState({ todos: [...this.state.todos, response.data] });
    });
  };

  removeTodo = (id) => {
    axios.delete(`/todos/${id}`).then(response => {
      this.setState({ todos: this.state.todos.filter(todo => todo.id !== id) });
    });
  };

  render() {
    return (
      <div>
        <h1>Todo App</h1>
        <input
          ref={input => this.input = input}
          placeholder="Enter a todo"
        />
        <button onClick={this.addTodo}>Add Todo</button>
        <ul>
          {this.state.todos.map(todo => (
            <li key={todo.id}>
              {todo.title}
              <button onClick={() => this.removeTodo(todo.id)}>Remove</button>
            </li>
          ))}
        </ul>
      </div>
    );
  }
}

export default App;
```

4. Start the React app:

`cd todo-app`
`npm start`

The app will then be available at http://localhost:3000.
