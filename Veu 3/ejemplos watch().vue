//Ejemplo 1
<script setup>
import { ref, watch } from 'vue'
const count = ref(0);
const message = ref('');

const addOne = () =>{
  count.value++;
};

watch(count, (newCount, oldCount) =>{
  message.value = `El valor del contador cambio de ${oldCount} a ${newCount}`;
});

</script>

<template>
  <h2>Cambio en el contador</h2>
  <p>Valor del contador: {{ count }}</p>
  <button @click="addOne">Sumar al contador</button>
  <p :style="{fontStyle:'italic'}">{{ message }}</p>
</template>

//Ejemplo 2

<script setup>
import { ref, watch } from 'vue'
const userName = ref('jose_m78');
const message = ref('');

const handleUserName = (event) =>{
  userName.value = event.target.value;
};

watch(userName, (newUserName, oldUserName) =>{
  message.value = `Seguro que deseas cambiar tu nombre de usuario de jose_m78 a ${newUserName}`;
});

</script>

<template>
  <h2>Cambio de nombre de usuario</h2>
  <p>Nombre de usuario: {{ userName }}</p>
  <input @input="handleUserName($event)" v-model="userName"/>
  <p>{{ message }}</p>
  <button>Guardar cambios</button>
  
</template>

//Ejemplo 3

<script setup>
import { ref, watch } from 'vue'
const firstName = ref('Juan');
const lastName = ref('Pérez');
const message = ref('');

const handleFirstName = (event) =>{
  firstName.value = event.target.value;
};

const handleLastName = (event) =>{
  lastName.value = event.target.value;
};


watch([firstName, lastName], ([newFirstName, newLastName], [oldFirstName, oldLastName]) => {
  message.value = `El nombre completo ha cambiado de Juan Pérez a ${newFirstName} ${newLastName}`;
});

</script>

<template>
  <h2>Cambio de datos</h2>
  <p>Nombre(s):</p>
  <input @input="handleFirstName($event)" v-model="firstName"/>
  <p>Apellidos:</p>
  <input @input="handleLastName($event)" v-model="lastName"/>
  <p>{{ message }}</p>
  
</template>