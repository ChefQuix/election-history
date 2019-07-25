<template>
	<v-app>
		<v-content>
			<v-tabs
				v-model="active"
				color="cyan"
				dark
				slider-color="yellow"
				v-if="$vuetify.breakpoint.smAndDown"
			>
				<v-tab v-for="type in types" :key="type.code">
					{{ type.type }}
				</v-tab>
				<v-tab-item v-for="type in types" :key="type.code">
					<YearSelector v-on:select-year="current_year = $event" :years="election_years"></YearSelector>
					<Geography :type="type.code" :year="current_year" />
				</v-tab-item>
			</v-tabs>
			<div v-if="$vuetify.breakpoint.mdAndUp">
				<Geography 
					v-for="type in types" 
					:key="type.code" 
					:type="type.code" 
					:year="current_year" />
			</div>
			
		</v-content>
	</v-app>
</template>

<script>
import Geography from './components/Geography'
import YearSelector from './components/YearSelector'

export default {
	name: 'App',
	components: {
		Geography, YearSelector
	},
	data () {
		return {
			active: 'A',
			types: [{code: 'A', type: 'Winnipeg and Brandon' },{ code: 'B', 'type': 'Manitoba'}],
			current_year: 1988,
			election_years: [2016, 2011, 2007, 2003, 1999, 1995, 1990, 1988, 1986, 1981, 1977, 1973, 1969, 1966, 1962, 1959, 1958],
			legend: {
				1958: [
					{
						party: 'Progressive Conservative',
						colour: '#0055fe',
					},
					{
						party: 'Liberal',
						colour: '#fe2037',
					},
					{
						party: 'CCF',
						colour: '#ffaa00',
					},
				],
				1962: [
					{
						party: 'Progressive Conservative',
						colour: '#0055fe',
					},
					{
						party: 'Liberal',
						colour: '#fe2037',
					},
					{
						party: 'New Democratic Party',
						colour: '#ffaa00',
					},
					{
						party: 'Social Credit',
						colour: '#10ff70',
					},
				],
				1973: [
					{
						party: 'Progressive Conservative',
						colour: '#0055fe',
					},
					{
						party: 'Liberal',
						colour: '#fe2037',
					},
					{
						party: 'New Democratic Party',
						colour: '#ffaa00',
					},
					]
				}
		}
	},

}
</script>
