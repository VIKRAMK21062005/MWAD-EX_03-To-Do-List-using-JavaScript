# MWAD-EX_03-To-Do-List-using-JavaScript
## Date:
### Reg no : 212222040180
### Name : Vikram K
## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
#### index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>To-Do</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <div class="todo">
    <h2>To-Do List</h2>
    <div class="input-group">
      <input type="text" id="taskInput" placeholder="Enter task..." />
      <button id="addBtn">Add</button>
    </div>

    <ul id="todoList" class="todo-list"></ul>
  </div>

  <script src="script.js"></script>
</body>
</html>
```

#### style.css
```
body {
    margin: 0;
    padding: 0;
    background: #f5f5f5;
    font-family: Arial, sans-serif;
  }
  
  .todo {
    max-width: 400px;
    margin: 60px auto;
    padding: 20px;
    background: white;
    border-radius: 10px;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
    background: #cbc6c6;
  }
  
  h2 {
    text-align: center;
    margin-bottom: 20px;
    color: #333;
  }
  
  .input-group {
    display: flex;
    gap: 10px;
  }
  
  input[type="text"] {
    flex: 1;
    padding: 8px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  button {
    padding: 8px 14px;
    font-size: 16px;
    background-color: #1976d2;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #125ea8;
  }
  
  .todo-list {
    list-style: none;
    padding: 0;
    margin-top: 20px;
  }
  
  .todo-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #eee;
  }
  
  .edit {
    margin-right: 5px;
    background-color: #fbc02d;
  }
  
  .delete {
    background-color: #e53935;
  }
  
  .edit:hover {
    background-color: #f9a825;
  }
  
  .delete:hover {
    background-color: #c62828;
  }
  ```
#### script.js
```
let todos = [];
let isEditing = false;
let editId = null;

const taskInput = document.getElementById("taskInput");
const addBtn = document.getElementById("addBtn");
const todoList = document.getElementById("todoList");

addBtn.addEventListener("click", () => {
  const task = taskInput.value.trim();
  if (task === "") return;

  if (isEditing) {
    todos = todos.map((todo) =>
      todo.id === editId ? { ...todo, text: task } : todo
    );
    isEditing = false;
    editId = null;
    addBtn.textContent = "Add";
  } else {
    todos.push({ id: Date.now(), text: task });
  }

  taskInput.value = "";
  renderTodos();
});

function renderTodos() {
  todoList.innerHTML = "";

  todos.forEach((todo) => {
    const li = document.createElement("li");
    li.className = "todo-item";
    li.innerHTML = `
      ${todo.text}
      <div>
        <button class="edit" onclick="editTodo(${todo.id})">Edit</button>
        <button class="delete" onclick="deleteTodo(${todo.id})">Delete</button>
      </div>
    `;
    todoList.appendChild(li);
  });
}

function deleteTodo(id) {
  todos = todos.filter((todo) => todo.id !== id);
  renderTodos();
}

function editTodo(id) {
  const item = todos.find((todo) => todo.id === id);
  taskInput.value = item.text;
  isEditing = true;
  editId = id;
  addBtn.textContent = "Update";
}
```

## OUTPUT

![image](https://github.com/user-attachments/assets/31b8a5de-34b4-4f3d-9c27-3adfcb0d3918)

## RESULT
The program for creating To-do list using JavaScript is executed successfully.
