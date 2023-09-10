<template>
  <div class="container">
    <h1>ToDo List</h1>
    <div>
      <input v-model="newTask" @keyup.enter="addTask" placeholder="Add a task..." />
    </div>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
        <button @click="removeTask(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'App',
  setup() {
    const newTask = ref('')
    const tasks = ref([])

    const addTask = () => {
      if (newTask.value) {
        tasks.value.push(newTask.value)
        newTask.value = ''
      }
    }

    const removeTask = (index) => {
      tasks.value.splice(index, 1)
    }

    return {
      newTask,
      tasks,
      addTask,
      removeTask
    }
  }
}
</script>

<style>
.container {
  max-width: 600px;
  margin: 40px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

h1 {
  text-align: center;
}

button {
  margin-left: 10px;
}
</style>
