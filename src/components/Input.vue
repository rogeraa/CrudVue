<template>
	<input
		type="text"
		class="form-control my-2"
		placeholder="Ingrese el nombre"
		v-model.trim="tarea.texto"
	/>
	<div class="form-check form-check-inline">
		<input
			class="form-check-input"
			type="checkbox"
			id="check-1"
			v-model="tarea.categorias"
			value="javascript"
		/>
		<label for="check-1" class="form-check-label">Javascript</label>
	</div>
	<div class="form-check form-check-inline">
		<input
			class="form-check-input"
			type="checkbox"
			id="check-2"
			v-model="tarea.categorias"
			value="node js"
		/>
		<label for="check-2" class="form-check-label">Node.js</label>
	</div>
	<div class="mt-2">
		<div class="form-check form-check-inline">
			<input
				type="radio"
				id="radio-1"
				class="form-check-input"
				value="urgente"
				v-model="tarea.estado"
			/>
			<label for="radio-1" class="form-check-label">Urgente</label>
		</div>
		<div class="form-check form-check-inline">
			<input
				type="radio"
				id="radio-1"
				class="form-check-input"
				value="relax"
				v-model="tarea.estado"
			/>
			<label for="radio-1" class="form-check-label">Relax</label>
		</div>
	</div>
	<div class="mt-2">
		<input type="number" v-model.number="tarea.numero" class="form-control" />
	</div>
	<button
		class="btn btn-dark mt-2 btn-block"
		type="submit"
		:disabled="bloquearBoton"
	>
		Procesar
	</button>
</template>

<script>
export default {
	props: {
		tarea: Object,
	},
	computed: {
		bloquearBoton() {
			return this.tarea.texto.trim() === '' ? true : false
		},
	},
}
</script>
