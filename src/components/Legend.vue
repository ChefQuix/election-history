<template>
	<v-layout align-start align-content-start row >
		<v-flex v-for="item in current_legend" :key="item.party" xs3 class="ma-1 pa-1">
			<div class="color-box" :style="'background-color: ' + item.colour + ';'"></div>
			{{ item.party }}
		</v-flex>
	</v-layout>
</template>

<script>
export default {
	props: ['legend', 'current_year'],
	computed: {
		current_legend() {
			let last = 0;
			for (var i in this.legend) {
				if (this.current_year == i) {
					return this.legend[i];
				} else if (this.current_year > i) {
					last = i;
				} else if (this.current_year < i) {
					return this.legend[last];
				}
			}
			return this.legend[last];
		}
	}
}
</script>

<style>
div.color-box { 
	width: 20px;
	height: 20px;
	margin: 5px;
	border: 1px solid rgba(0, 0, 0, .2);
}
</style>