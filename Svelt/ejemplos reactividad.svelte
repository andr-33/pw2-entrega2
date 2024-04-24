//Ejemplo No. 1

<script>
    //Declaramos una varible reactiva, con let es automatica la reactividad
	let state = false;

    //Funcion que modifica el estado de la variable "state", se llama mediante el evento on:click
	const toggleState = () =>{
		state = !state;
	};
</script>

<h2>Cambio de estado</h2>
<p>Pulsa el botón!</p>
<button 
	on:click={toggleState}
	class="button {state? 'active-button':'deactivate-button'}"
>
	{state ? 'ACTIVO': 'DESACTIVO'}
</button>

<style>
	.button{
		padding: 20px;
		width: 120px;
	}

	.active-button{
		background-color: green;
	}

	.deactivate-button{
		background-color: red;
	}
</style>

//Ejemplo No. 2

<script>
  import { writable } from 'svelte/store';

  //Con writable podemos crear objetos reactivos

  const formData = writable({
    username: '',
    password: ''
  });


  //Funcion que permite manejar los cambios en cada atributo del objeto formData
  function handleChange(event) {
    formData.update(data => ({
      ...data,
      [event.target.name]: event.target.value
    }));
  }
</script>

<input type="text" bind:value={$formData.username} name='username' on:input={handleChange} placeholder="Usuario">
<input type="password" bind:value={$formData.password} name='password' on:input={handleChange} placeholder="Contraseña">

<p>Usuario: {$formData.username}</p>
<p>Contraseña: {$formData.password}</p>