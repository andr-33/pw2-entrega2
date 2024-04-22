//Ejemplo No. 1

<script setup>
  import {ref} from "vue"
  const count = ref(0);
  
  const increment = () => {
    count.value++;
  };
  
</script>

<template>
  <p>{{count}}</p>
  <button @click="increment">Click!</button>
</template>


//Ejemplo No. 2

<script setup>
   import {ref} from "vue"

  const inputValue = ref("");

  const handleValueChange = (event) =>{
    inputValue.value = event.target.value;
  };
  
</script>

<template>
 <input @input="handleValueChange($event)" placeholder="User name" />
 <p>Value: {{ inputValue }}</p>
</template>

//Ejemplo No. 3

<script setup>
   import {ref} from "vue"

  const isActive = ref(false);

  const toggle = () =>{
    isActive.value = !isActive.value
  };
  
</script>

<template>
 <button @click="toggle" 
 :style="{backgroundColor:  isActive ? 'green' : 'red', }">Turn {{ isActive ? "on" : "off" }} </button>
</template>
