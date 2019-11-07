<template>
	<div>
	  	<div v-bind:class="{ 'lighten': !item.viewed, 'lighten-2': item.viewed }" class="card blue-grey">
	        <div class="card-content black-text">
	          <span class="card-title white-text">{{ item.id }}. {{ item.title | capitalize }}</span>
	          <p class="white-text">{{ item.description | capitalize  }}</p>
	        </div>

	        <div class="card-action blue-grey lighten viewed-buttons">
	          <a @click="toogleView" v-bind:class="{ disabled: editing }" href="javascript:void(0);" class="white-text small-text">
	          	<small>	
		          	<span v-if="item.viewed">Marcar para ver</span>
		          	<span v-if="!item.viewed">Marcar como vista</span>
	          	</small>
		      </a>
		      <span class="buttons right">
	          	<a @click="editItem" v-bind:class="{ disabled: editing }" href="javascript:void(0);" title="Editar" class="white-text">
			    		<i class="material-icons">edit</i>
			      </a>
	          	<a @click="removeItem" v-bind:class="{ disabled: editing }" href="javascript:void(0);" title="Eliminar" class="white-text">
			    		<i class="material-icons">delete_forever</i>
			      </a>
		      </span>
	        </div>
	    </div>
	</div>
</template>



<script>
	export default {
		name: 'card',

		props: ['editing', 'item'],

		components: {},

		methods: {
			toogleView() {
				if(!this.editing){
					this.item.viewed = !this.item.viewed;
				}
			},

			editItem() {
				if(!this.editing){
					this.$emit('editItem', this.item);
				}
			},

			removeItem() {
				if(!this.editing){
					this.$emit('removeItem', this.item);
				}
			},
		},
	}
</script>