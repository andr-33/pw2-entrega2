//Ejemplo No. 1

<script setup>
  import {ref, computed} from "vue"

  const width = ref(0);
  const height = ref(0);

  const area = computed(() => {
    return width.value * height.value;
  });

  const handleWidth = (event) =>{
    width.value = event.target.value;
  };
  const handleHeight = (event) =>{
    height.value = event.target.value;
  };
  
</script>

<template>
  <h2>Area de un rectangulo</h2>
  <p>Dimensiones del rectangulo: </p>
  <input @input="handleWidth($event)" placeholder="Ancho" />
  <input @input="handleHeight($event)" placeholder="Alto" />
  <p>Area del rectangulo: {{ area }}</p>
</template>

//Ejemplo No. 2

<script setup>
  import {ref, computed} from "vue"

  const items = ref([
    { name: 'Manzanas', price: 2 },
    { name: 'Plátanos', price: 3 },
    { name: 'Naranjas', price: 2.5 }
  ]);

  const total = computed(() => {
    return items.value.reduce((acc, item) => acc + item.price, 0);
  });
  
</script>

<template>
  <h2>Total lista de la compra</h2>
  <div v-for="item in items">
    {{ item.name }} a €{{ item.price }}
  </div>
  <p>Total: €{{ total }}</p>
</template>

//Ejemplo No. 3

<script setup>
import { ref, computed } from 'vue'

const password = ref('');

const isStrongPassword = computed(() => {
  return password.value.length >= 8 && /[a-z]/.test(password.value) && /[A-Z]/.test(password.value) && /\d/.test(password.value);
});

const handlePassword = (event) =>{
  password.value = event.target.value;
};

</script>

<template>
  <h2>Validador de contraseña</h2>
  <form :style="{display:'flex', flexDirection:'column', width:'200px'}">
    <p>Contraseña:</p>
    <input 
     type="text" 
     placeholder="Ingresa tu contraseña" 
     @input="handlePassword($event)"
     v-model="password"
    />
    <button :style="{marginTop:'5px'}">Ingresar</button>
    <p :style="{color: isStrongPassword ? 'green':'red', textAlign: 'center'}">
      {{ isStrongPassword ? 'Contraseña segura' : 'Contraseña insegura'}}
    </p>
  </form>
</template>
