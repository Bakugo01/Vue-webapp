<script setup>
import { ref } from 'vue'

const show = ref(true)
const list = ref([1, 2, 3])
</script>

<template>
  <div class="container">
    <div class="body-text">
      <button @click="show = !show">Toggle List</button>
      <button @click="list.push(list.length + 1)">Push Number</button>
      <button @click="list.pop()">Pop Number</button>
      <button @click="list.reverse()">Reverse List</button>
      <ul v-if="show && list.length">
        <li v-for="item in list" :key="item">{{ item }}</li>
      </ul>
      <p v-else-if="list.length">List is not empty, but hidden.</p>
      <p v-else>List is empty.</p>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f0f0f0; 
}

.body-text {
  text-align: center;
  padding: 20px;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

button {
  margin: 5px;
  padding: 10px 15px;
  font-size: 16px;
  cursor: pointer;
  border: 1px solid #ccc;
  border-radius: 4px;
  background-color: #f4f4f4;
}

button:hover {
  background-color: #e0e0e0;
}

ul {
  list-style-type: none;
  padding-left: 0;
}

li {
  margin: 5px 0;
}
</style>
