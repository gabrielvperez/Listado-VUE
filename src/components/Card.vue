<template>
	<div>


	  	<div v-bind:class="{ 'lighten': !item.viewed, 'lighten-2': item.viewed }" class="card blue-grey">
	        <div class="card-content black-text">
	          <span class="card-title white-text">{{ item.title }}</span>
	          <p class="white-text">{{ item.description }}</p>
	        </div>

	        <div class="card-action blue-grey lighten">
	          <a v-on:click="toogleView" href="javascript:void(0);" class="white-text small-text">
	          	<small>	
		          	<span v-if="item.viewed">Marcar para ver</span>
		          	<span v-if="!item.viewed">Marcar como vista</span>
	          	</small>
		      </a>
		      <span class="buttons right">
		          <a v-on:click="deleteMovie" href="javascript:void(0);" title="Eliminar" class="white-text">
				    <i class="material-icons">delete_forever</i>
			      </a>
		      </span>
	        </div>
	    </div>
	  	

	</div>
</template>

<script>
import Add from "../components/Add"

export default {
	name: 'card',
	props: ['list', 'item'],
	components: {
		Add
	},
	methods: {
		toogleView: function () {
			this.item.viewed = !this.item.viewed
		},
		deleteMovie: function () {
  			this.list.splice(this.list.indexOf(this.item), 1)
		}
	}
}
</script>

<style type="text/css">
	.buttons a {
		margin-right: 0px !important;
	}
</style>