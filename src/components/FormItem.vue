<template>
	<div>

		<br>

		<form @submit.prevent="saveItem">
	      <div class="row">
	        	<div class="input-field col s6">
  					<input type="text" v-model="item.title" id="title" name="title" class="validate" required>
          		<label for="title">Título película</label>
          		<span data-error="* Campo obligatorio" class="helper-text"></span>
	        	</div>
	        	<div class="input-field col s6">
        			<input type="text" v-model="item.description" id="description" name="description" class="validate" required>
	          	<label for="description">Descripción película</label>
          		<span data-error="* Campo obligatorio" class="helper-text"></span>
	        	</div>

				<div class="input-field col s12 center-align">
					<button @click.prevent="cancelItem" v-if="!item.id && (item.title || item.description)" class="btn waves-effect waves-light grey">Limpiar
						<i class="material-icons left">close</i>
					</button>
					<button @click.prevent="cancelItem" v-if="item.id" class="btn waves-effect waves-light grey">Cancelar
						<i class="material-icons left">chevron_left</i>
					</button>
					<button type="submit" v-if="item.id" class="btn waves-effect waves-light blue">Guardar cambios
						<i class="material-icons left">save_alt</i>
					</button>
					<button type="submit" v-if="!item.id" class="btn waves-effect waves-light blue">Añadir película
						<i class="material-icons left">add</i>
					</button>
				</div>
	      </div>
		</form>
	</div>
</template>



<script>
	export default {
	  	name: 'formItem',

	  	props: ['itemMock', 'item'],

	  	data() {
			return {}
	  	},

		methods: {
			cancelItem() {
				this.$emit('cancel');
			},

			saveItem() {
				this.$emit('save', this.item);
			},
		},
	}
</script>