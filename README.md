# 📝 ToDo App using ReactJS

A simple yet functional To-Do List application built with **ReactJS** (using class-based components) and styled with **React-Bootstrap**.
**Live:** **https://todo-list-113.netlify.app/**
## 🚀 Features
- ✅ Add new tasks
- 🗑️ Delete tasks by clicking the delete button
- ✏️ Edit existing tasks using a prompt
- 🎨 Clean and responsive UI with Bootstrap styling

---

## 📦 Tech Stack
- ReactJS (Class Components)
- Bootstrap 5
- React-Bootstrap

---

## 📁 Folder Setup
Bootstrapped using `create-react-app`. The folder structure follows the standard CRA layout.

**Key dependencies in `package.json`:**
```json
"react": "^18.2.0",
"bootstrap": "^5.3.0",
"react-bootstrap": "^2.7.4",
"react-dom": "^18.2.0",
"react-scripts": "5.0.1"
```

---

## 💻 How to Run

```bash
# Clone the repo
git clone https://github.com/your-username/todo-react.git
cd todo-react

# Install dependencies
npm install

# Run the development server
npm start
```

Then open your browser at: [http://localhost:3000](http://localhost:3000)

---

## 📄 App.js Code

```jsx
import React, { Component } from "react";
import "bootstrap/dist/css/bootstrap.css";
import Container from "react-bootstrap/Container";
import Row from "react-bootstrap/Row";
import Col from "react-bootstrap/Col";
import Button from "react-bootstrap/Button";
import InputGroup from "react-bootstrap/InputGroup";
import FormControl from "react-bootstrap/FormControl";
import ListGroup from "react-bootstrap/ListGroup";

class App extends Component {
    constructor(props) {
        super(props);
        this.state = {
            userInput: "",
            list: [],
        };
    }

    updateInput(value) {
        this.setState({ userInput: value });
    }

    addItem() {
        if (this.state.userInput !== "") {
            const userInput = {
                id: Math.random(),
                value: this.state.userInput,
            };

            const list = [...this.state.list];
            list.push(userInput);

            this.setState({
                list,
                userInput: "",
            });
        }
    }

    deleteItem(key) {
        const list = [...this.state.list];
        const updateList = list.filter((item) => item.id !== key);
        this.setState({ list: updateList });
    }

    editItem = (index) => {
        const todos = [...this.state.list];
        const editedTodo = prompt('Edit the todo:');
        if (editedTodo !== null && editedTodo.trim() !== '') {
            todos[index].value = editedTodo;
            this.setState({ list: todos });
        }
    }

    render() {
        return (
            <Container>
                <Row className="text-center my-4">
                    <h1>TODO LIST</h1>
                </Row>
                <Row>
                    <Col md={{ span: 5, offset: 4 }}>
                        <InputGroup className="mb-3">
                            <FormControl
                                placeholder="Add item..."
                                size="lg"
                                value={this.state.userInput}
                                onChange={(item) => this.updateInput(item.target.value)}
                            />
                            <Button
                                variant="dark"
                                className="mt-2"
                                onClick={() => this.addItem()}
                            >
                                ADD
                            </Button>
                        </InputGroup>
                    </Col>
                </Row>
                <Row>
                    <Col md={{ span: 5, offset: 4 }}>
                        <ListGroup>
                            {this.state.list.map((item, index) => (
                                <div key={item.id}>
                                    <ListGroup.Item
                                        variant="dark"
                                        action
                                        className="d-flex justify-content-between align-items-center"
                                    >
                                        {item.value}
                                        <span>
                                            <Button
                                                variant="light"
                                                className="me-2"
                                                onClick={() => this.deleteItem(item.id)}
                                            >
                                                Delete
                                            </Button>
                                            <Button
                                                variant="light"
                                                onClick={() => this.editItem(index)}
                                            >
                                                Edit
                                            </Button>
                                        </span>
                                    </ListGroup.Item>
                                </div>
                            ))}
                        </ListGroup>
                    </Col>
                </Row>
            </Container>
        );
    }
}

export default App;
```

---

## 📅 Last Updated
**09 Jan, 2025**
