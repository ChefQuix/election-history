<template>
<div>
	<v-layout align-start align-content-start flex>
		<v-flex v-for="item in current_legend" :key="item.party" xs3 class="ma-1 pa-1">
			<div class="color-box" :style="'background-color: ' + item.colour + ';'"
			></div>
			{{ item.party }}
		</v-flex>
	</v-layout>
	<LegendDetail 
		:legend_year="legend_year" 
	></LegendDetail>
</div>
</template>

<script>
import LegendDetail from '@/components/LegendDetail'

export default {
	components: { LegendDetail },
	props: ['legend', 'current_year'],
	data() {
		return {
			open_more_info: false,
		}
	},
	computed: {
		legend_year() {
			let last = 0;
			for (var i in this.legend) {
				if (this.current_year == i) {
					return i;
				} else if (this.current_year > i) {
					last = i;
				} else if (this.current_year < i) {
					return last;
				}
			}
			return last;
		},

		current_legend() {
			return this.legend[this.legend_year];
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