<template>
	<h3 class="m-2">Editando el id: {{ $route.params.id }}</h3>
	<form @submit.prevent="updateTarea(tarea)">
		<Input :tarea="tarea" />
	</form>
</template>

<script>
import { mapState, mapActions } from 'vuex'
import Input from '../components/Input.vue'
export default {
	components: {
		Input,
	},
	computed: {
		...mapState(['tarea']),
	},
	methods: {
		...mapActions(['setTarea','updateTarea']),
	},
	created() {
		this.setTarea(this.$route.params.id)
	},
}
</script>
