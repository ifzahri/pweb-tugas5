<template>
    <div class="container-fluid">
      <div class="p-5 mb-4 text-bg-dark border rounded-3">
        <div class="container-fluid py-5">
          <h1 class="display-5 fw-bold">Todo List</h1>
          <input type="text" class="form-control" id="task" v-model="newTask" @keyup.enter="addTask" placeholder="Add a new task" />
        </div>
      </div>
      <div class="container-fluid py-5" id="todo-list">
        <ul>
          <li v-for="(task, index) in tasks" :key="index" @click="toggleTask(index)" :class="{ completed: task.completed }">
            {{ task.text }}
            <button @click="removeTask(index)">Remove</button>
          </li>
        </ul>
      </div>
    </div>
  </template>
  
  <style scoped>
  .completed {
    background-color: white;
    color: black;
    text-decoration: line-through;
    cursor: pointer;
  }
  </style>
  
  <script>
  export default {
    data() {
      return {
        newTask: '',
        tasks: []
      };
    },
    methods: {
      addTask() {
        if (this.newTask.trim() !== '') {
          this.tasks.push({ text: this.newTask, completed: false });
          this.newTask = '';
        }
      },
      removeTask(index) {
        this.tasks.splice(index, 1);
      },
      toggleTask(index) {
        this.tasks[index].completed = !this.tasks[index].completed;
      }
    }
  };
  </script>
  