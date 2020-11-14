<template>
  <div>
    <div class="input-container">
      <input type="text" v-model="newName" @keydown.enter="addNewTask" placeholder="John Doe" class="name-input">
      <input type="text" v-model="newTask" @keydown.enter="addNewTask" placeholder="Excercise">
    </div>
    <div class="input-info">
      <div>
        {{"You have " + taskId + " unfinished task/s"}}
      </div>
      <div>
       <small>double click to </small><a @dblclick="deleteAll">delete all</a>
      </div>
    </div>
    <hr>
    <div class="todo-container" v-for="(todo, index) in todos" :key="index">
      <div class="todo-left">
        <div >
          <h4>{{todo.name}}</h4>
        </div>
        <div class="task-container">
          <!-- {{todo.count + ":"}} --> {{todo.task}}
        </div>
      </div>
      <div class="todo-right" @click="deleteTask(index)">
        <p class="task-delete">&times;</p>
      </div>
    </div>
    <hr>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newName: '',
      newTask: '',
      taskId: 0,

      todos: []
    }
  },
  methods: {
    addNewTask() {
      if(this.newTask.trim().length == 0) {
        return
      }
      if(this.newName.trim().length == 0) {
        this.newName = "not specified"
      }
      this.todos.push(
        {
          id: this.taskId,
          count: 1 + this.taskId,
          name: this.newName,
          task: this.newTask,
          completion: false
        }
      )
      this.newTask = '',
      this.taskId++
    },
    deleteTask(index) {
      this.todos.splice(index, 1)
      this.taskId--
    },
    deleteAll() {
      this.todos = []
      this.taskId = 0
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.input-container {
  box-sizing: border-box;
  margin: 0 auto;

  .name-input {
    width: 30%;
    margin-bottom: 10px;
    text-align: center;
  }

  input {
    width: 100%;
    height: 5vh;
    border: none;
    border-bottom: 1px solid black;

    &:focus {
      outline: none;
    }
  }
}
.input-info {
  display: flex;
  margin-top: 20px;
  justify-content: space-between;

  a {
    cursor: pointer;
    -moz-user-select: -moz-none;
    -khtml-user-select: none;
    -webkit-user-select: none;
    -ms-user-select: none;
    user-select: none;

    &:hover {
      color: red;
    }
  };
}
.todo-container {
  display: flex;

  .todo-left {
    margin-right: auto;
    margin: auto 0;

    h4, .task-container {
      text-align: left;
      margin-bottom: 5px;
    };
  }
  .todo-right {
    margin-left: auto;

    .task-delete {
      cursor: pointer;

      &:hover {
        color: red;
      }
    }
  }
}
</style>

// TODOS
// create username input that you only have to input once === true
// input field for tasks
// button for more submit options
// fix task id deletion

// TODOS STYLE
// make the site more responsive
// scrollable div for all tasks - not scrollable website

