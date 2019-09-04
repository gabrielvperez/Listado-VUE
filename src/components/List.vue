<template>  
	<div>


		<div class="row">
			<transition-group name="list" tag="div">
				<div v-for="item in list" v-bind:key="item.id" class="col s4">
					<card :list="list" :item="item"></card>
				</div>
			</transition-group>
		</div>


	</div>
</template>

<script>
import Card from "../components/Card"

export default {
	name: 'list',
	props: ['list'],
	components: {
		Card
	}
}
</script>

<style type="css">
	.list-enter-active, 
	.list-leave-active {
  		transition: all 1s;
	}
	.list-enter, .list-leave-to {
	  	opacity: 0;
	  	transform: translateX(30px);
	}
</style>