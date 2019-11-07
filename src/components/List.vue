<template>  
	<div>
		<div class="row">
			<transition-group name="list" tag="div">
				<div v-for="item in items" :key="item.id" class="col s4">
					<item :item="item" :editing="editing" @editItem="editItem" @removeItem="removeItem"></item>
				</div>
			</transition-group>
		</div>
	</div>
</template>



<script>
	import Item from "../components/Item"

	export default {
		name: 'list',

		props: ['editing', 'items'],

		components: {
			Item,
		},

		methods: {
			editItem(_item) {
				this.$emit('edit', _item);
			},

			removeItem(_item) {
				this.$emit('remove', _item);
			},
		},
	}
</script>