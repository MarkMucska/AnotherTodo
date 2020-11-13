<template>
  <div>
    <div class="input-container">
      <input type="text" v-model="newTask" @keydown.enter="addNewTask">
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
       {{todo.count + ":"}} {{todo.task}}
      </div>
      <div class="todo-right" @click="deleteTask(index)">
        <p class="task-delete">&times;</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
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
      this.todos.push(
        {
          id: this.taskId,
          count: 1 + this.taskId,
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

  input {
    width: 100%;
    height: 5vh;

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
// create username input that you only have to input once
// input field for tasks
// button for more submit options
// fix task id deletion

// TODOS STYLE
// make the site more responsive
// scrollable div for all tasks - not scrollable website

