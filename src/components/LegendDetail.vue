<template>
<div>
	<v-btn small color="cyan" text dark
	@click.stop="show_dialog = true"
	class="details-btn"
	>
	Legend
	</v-btn>
	<v-dialog
	  v-model="show_dialog"
	  max-width="250"
	  >
		<v-card>
			<v-card-title class="headline">Legend Details</v-card-title>
			<v-card-text>
				<img :src="legend_image" />
			</v-card-text>
			<v-card-actions>
				<v-btn
					color="cyan"
					text
					dark
					@click="show_dialog = false"
				>
				Close
				</v-btn>
			</v-card-actions>
		</v-card>
	</v-dialog>
</div>
</template>

<script>
export default {
	data() {
		return {
			show_dialog: false,
		}
	},

	props: ['legend_year'],

	computed: {
		legend_image() {
			return require('@/assets/legend_' + this.legend_year + '.png');
		} 
	},

}
</script>

<style>
@media only screen and (min-width: 960px) {
	button.details-btn {
	   margin-bottom: 1em; 
	}
}
</style>