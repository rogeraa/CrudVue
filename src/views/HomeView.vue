<template>
	<h2 class="mt-2 mb-2">Formulario con vue.js</h2>
	<form @submit.prevent="procesarFormulario">
		<Input :tarea="tarea" />
	</form>
	<ListaTareas />
</template>

<script>
import Input from '../components/Input.vue'
import ListaTareas from '../components/ListaTareas.vue'
import { mapActions } from 'vuex'
const shortid = require('shortid')
// @ is an alias to /src

export default {
	name: 'HomeView',
	components: {
		Input,
		ListaTareas,
	},
	data() {
		return {
			tarea: {
				id: '',
				texto: '',
				categorias: [],
				estado: '',
				numero: 0,
			},
		}
	},
	methods: {
		...mapActions(['setTareas']),
		procesarFormulario() {
			console.log(this.tarea)
			if (this.tarea.texto.trim() === '') {
				console.log('Campo vacio')
				return
			}
			console.log('No esta vacio')
			//Generamos el id
			this.tarea.id = shortid.generate()
			console.log(this.tarea.id)

			// enviar datos
			this.setTareas(this.tarea)
			this.tarea = {
				id: '',
				texto: '',
				categorias: [],
				estado: '',
				numero: 0,
			}
		},
	},
}
</script>
