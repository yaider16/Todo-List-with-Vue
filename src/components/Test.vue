<template>
	<h2>Coche Poder</h2>
	<p>Power: {{power}}</p>
	<button @click="aumentar">Aumentar</button>
	<button @click="disminuir">Disminuir</button>
	<button @click="reestablecer">Reestablecer</button>
</template>

<script>
	/* El ref sirve para ayudar a visualizar en el doc directamente sin tener que actualizar la page   */
	import { ref } from "vue";
export default {
	props:{
		power: {type: Number, default: 40},
		aumentar: Function,
		disminuir: Function
	},
	setup(props){
		const saludo = "Hola que hace";


		console.log(props);
		return {saludo}


	}
}
</script>

<style lang="css" scoped>
</style>