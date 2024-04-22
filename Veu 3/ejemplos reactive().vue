//Ejemplo No. 1

<script setup>
  import {reactive} from "vue"

  const formData = reactive({
    username: '',
    password: ''
  });

  const handleChange = (event) => {
    formData[event.name] = event.target.value
  };
  
</script>

<template>
 <h2>Sign UP :)</h2>
 <form :style="{display: 'flex', flexDirection: 'column', width: '200px', gap: '10px'}">
  <input type="text" @input="handleChange($event)" placeholder="Username" name="username" v-model="formData.username"/>
  <input type="password" @input="handleChange($event)" placeholder="Password" name="password" v-model="formData.password"/>
 </form>
</template>

//Ejemplo No. 2

<script setup>
  import {reactive} from "vue"

  const taskList = reactive([
    { id: 1, title: 'Hacer la compra', completed: false },
    { id: 2, title: 'Llamar al banco', completed: false },
    { id: 3, title: 'Estudiar Vue.js', completed: true }
  ]);

  const toggleTaskStatus = (taskId) => {
    const task = taskList.find(task => task.id === taskId);
    if (task) {
      task.completed = !task.completed;
    }
  };
  
</script>

<template>
  <h2>Lista de tareas</h2>
 <div :style="{display: 'flex', flexDirection: 'column'}">
  <div v-for="task in taskList" :key="task.id">
    {{ task.title }}
    <button @click="toggleTaskStatus(task.id)">{{ task.completed ? "Hecho" : "Pendiente" }}</button>
  </div>
 </div>
</template>