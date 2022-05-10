<template>
	<table class="table mt-2">
		<thead class="thead-dark">
			<tr>
				<th scope="col">#</th>
				<th scope="col">Nombre</th>
				<th scope="col">Categorias</th>
				<th scope="col">Estado</th>
				<th scope="col">Número</th>
				<th scope="col">Accion</th>
			</tr>
		</thead>
		<tbody>
			<tr v-for="item in tareas" :key="item.id">
				<th scope="row">{{ item.id }}</th>
				<td>{{ item.texto }}</td>
				<td>
					<span v-for="(cat, index) in item.categorias" :key="index">
						{{ item.categorias.length === index + 1 ? cat : cat + ', ' }}
					</span>
				</td>
				<td>{{ item.estado }}</td>
				<td>{{ item.numero }}</td>
				<td>
					<button class="btn btn-danger btn-sm" @click="deleteTarea(item.id)">
						<i class="bi bi-trash"></i>
					</button>
					<router-link
						class="btn btn-warning ml-2 btn-sm"
						:to="{
							name: 'Editar',
							params: {
								id: item.id,
							},
						}"
					>
						<i class="bi bi-pencil"></i>
					</router-link>
				</td>
			</tr>
		</tbody>
	</table>
</template>

<script>
import { mapState, mapActions } from 'vuex'
export default {
	computed: {
		...mapState(['tareas']),
	},
	methods: {
		...mapActions(['deleteTarea']),
	},
}
</script>
