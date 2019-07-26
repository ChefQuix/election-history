<template>
	<v-layout align-start justify-space-between row >
		<v-flex v-for="item in current_legend" :key="item.party">
			<div class="color-box" :style="'background-color: ' + item.colour + ';'">&nbsp;</div>
			{{ item.party }}
		</v-flex>
	</v-layout>
</template>

<script>
export default {
	props: ['legend', 'current_year'],
	/*
	data() {
		return {
			current_legend: {},
		}
	},
	
	methods: {
		set_current_legend(year) {
			for (var i in this.legend) {
				if (year <= i) {
					return this.legend[i];
				}
			}
			return this.current_legend[0];
	
		}

	},
	watch: {
		current_year(year) {
			this.set_current_legend(year);
		}
	},
	*/
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
	float: left;
	width: 20px;
	height: 20px;
	margin: 5px;
	border: 1px solid rgba(0, 0, 0, .2);
}
</style>