<template>
	<div>

		<br>

		<form @submit="addItem">
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
				  	<button class="btn waves-effect waves-light blue-grey" type="submit">Añadir película
				   	<i class="material-icons left">add</i>
				  	</button>
	        	</div>
            <div v-if="error" class="input-field col s12 center-align">
	         	<span class="red-text">{{ error }}</span>
	        </div>
	      </div>
		</form>


	</div>
</template>

<script>
const emptyItem = {	
	title: null,
	description: null,
	viewed: false
}

export default {
  	name: 'add',
  	props: ['list'],
  	data: () => {
		return {
			error: null,
			id: 1,
			item: Object.assign({}, emptyItem),
		}
  	},
	methods: {
		validateForm: function () {
	      this.error = null;

	      if (!this.item.title || !this.item.description) {
	         this.error = '* Faltan campos obligatorios'
         	return false;
	      }
        return true;
		},
		addItem: function (_e) {
			_e.preventDefault()

			if(this.validateForm()){
				this.list.push({
						id: this.id++, 
						title: this.item.title, 
						description: this.item.description,
						viewed: this.item.description.viewed
				})
				// Clean form
	      	this.error = null;
				this.item = Object.assign({}, emptyItem);
      	}
		}
	}
}
</script>