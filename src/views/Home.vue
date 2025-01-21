<script setup>
import { ref } from 'vue';

const message = ref('Hello World');
</script>

<template>
  <div class="app">
    <h1>Vue.js Yo-Do List</h1>
    <input v-model="newTask" placeholder="Add a new task" @keyup.enter="addTask" />
    <button @click="addTask">Add Task</button>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <input type="checkbox" v-model="task.completed" />
        <span :class="{ 'completed-task': task.completed }">{{ task.text }}</span>
        <button @click="removeTask(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

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
      if (this.newTask.trim()) {
        this.tasks.push({ text: this.newTask, completed: false });
        this.newTask = ''; 
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    }
  }
};
</script>

<style scoped>
.app {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  text-align: center;
  padding: 20px;
  color: #b3007d; 
  background-image: url('src/img/des.jpg');
  background-size: cover;
  background-position: auto;
}

input, button {
  margin: 14px 0;
  padding: 17px;
  font-size: 18px;
  border-radius: 6px;
  border: 1px solid #03d9e9; 
}

button {
  background-color: #e611b0; 
  color: white; 
  cursor: pointer;
}

button:hover {
  background-color: #ff0000; 
}

ul {
  list-style-type: none;
  padding: 0;
  margin: 20px 0;
}

li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: rgba(255, 255, 255, 0.8); 
  padding: 18px;
  border-radius: 8px;
  margin: 6px 0;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1); 
}

.completed-task {
  text-decoration: line-through;
  color: #A0A0A0; 
}

@media only screen and (min-width: 600px) {
  .head {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    text-align: center;
    color: #fc0000; 
    margin-top: 50px;
    margin-left: auto;
    margin-right: auto;
  }
}

@media only screen and (min-width: 768px) {
  .head {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    text-align: center;
    color: #fa0000; 
  }
}

@media only screen and (min-width: 992px) {
  .head {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    text-align: center;
    color: #ffffff; 
  }
}

@media only screen and (min-width: 1200px) {
  .head {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    text-align: center;
    color: #ffffff; 
  }
}
</style>