<template>
	<div class="container">
		<h2 class="text-center mt-5">My Vue todo app</h2>

		<!-- Input -->
		<div class="d-flex">
			<input v-model="task" type="text" class="form-control" placeholder="Enter Any Text">
			<button class="btn btn-warning rounded-0" @click="submitTask">SUBMIT</button> 
		</div>

		<div class="table">
			<!-- Task Table --->
			<table class="table table-bordered mt-5">
			  <thead>
			    <tr>
			      <th scope="col">Tarea</th>
			      <th scope="col">Estado</th>
				  <th scope="col">#</th>
			  	  <th scope="col">#</th>    
			    </tr>
			  </thead>
			  <tbody v-for="(task, index) in tasks" :key="index">
			    <tr>
			      <td>{{ task.name }}</td>
			      <td>
			      	<span class="pointer" @click="changeStatus(index)">{{ task.status }}</span>
			      </td>
			      <td>
			      	<div class="text-center" @click="edit(index)">
			      		<span class="fas fa-pen"></span>
			      	</div>
			      </td>
			      <td>
			      	<div class="text-center" @click="Delete(index)">
			      		<span class="fas fa-trash" id="on"></span>
			      	</div>
			      </td>
			    </tr>
			  </tbody>
			</table>
		</div>
	</div>
</template>

<script>
export default {
  name: 'TodoApp',
    data(){
    	return{
    		task: '',
		    tasks:[],
		    editTask: null,
		    availableStatuses: ['to-do', 'in-progress', 'finished'],
		}
	},

	methods:{
		submitTask(){
			// Dice que si en el input nmo hay nada pos no agrega nada
			if (this.task.length === 0 ) return;

			// Dice que si se puede editar es null pos tonces no edita, sino que crea una nueva tabla
			if(this.editTask == null){
				this.tasks.push({name: this.task, status: 'Hacer'})
				this.task = ''				
			}
			// Aqui dice que si lo de arriba es mentira osea no es null va a el array tasks va a coger el indice que tenga editTask en el momento y coge el nombre y se lo asigna a el input finalmente hace que editTask vuelva a ser null 
			else{
				this.tasks[this.editTask].name = this.task;
				this.editTask = null;
				this.task = '';
				console.log(this.editTask);
			}

		},

		// El metodo splice cambia el contenido de un array añadiendo o removiendo elementos existentes en un objeto
		Delete(index){
			this.tasks.splice(index,1);
		},

		// Aqui obtiene el indice de la tarea y dice que este sera igual a el nombre que tiene el indice en el array tasks y luego hace que editTask sea igual a el indice 
		edit(index){
			this.task = this.tasks[index].name;
			this.editTask = index
			console.log(this.editTask);
		},


		// El indexOf devuelve el indice de el objeto pedido ose que ahí está pidiendo un indice que es el estado del indice por ejemplo si el indice es 1 devuelve el estado que tiene el ibjeto con indice uno. con esa informacion comprueba si el nuevo indice que creamos es mayor a 2 lo devuelve a cero para mantener un ciclo
		changeStatus(index){
			let newIndex =this.availableStatuses.indexOf(this.tasks[index].status);
			newIndex++;
			if(newIndex > 2){newIndex = 0;}
			console.log(newIndex);
		}
	}
}



</script>



<style lang="css" scoped>
	#on{
		cursor: pointer;
		transition: all .2s ease;
	}
	#on:hover{
		transform: scale(1.2);
	}

	.pointer{cursor: pointer;}
</style>