<template>
	<v-app>
		<v-content>
			<v-container fluid>

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
						<v-layout align-start justify-space-between row >
							<v-flex xs3>
								<YearSelector v-on:select-year="current_year = $event" :years="election_years"></YearSelector>
							</v-flex>
							<v-flex xs9>
								<Legend :legend="legend" :current_year="current_year"></Legend>
								<Geography :type="type.code" :year="current_year" />
							</v-flex>
						</v-layout>
					</v-tab-item>
				</v-tabs>

				<div v-if="$vuetify.breakpoint.mdAndUp">
						<Legend :legend="legend" :current_year="current_year"></Legend>
						<v-layout align-start justify-space-between row >
							<v-flex>
					<YearSelector v-on:select-year="current_year = $event" :years="election_years"></YearSelector>
							</v-flex>
							<v-flex>
					<Geography 
						v-for="type in types" 
						:key="type.code" 
						:type="type.code" 
						:year="current_year" />
							</v-flex>
						</v-layout>
				</div>
			</v-container>	
		</v-content>
	</v-app>
</template>

<script>
import Geography from '@/components/Geography'
import YearSelector from '@/components/YearSelector'
import Legend from '@/components/Legend'

export default {
	name: 'App',
	components: {
		Geography, YearSelector, Legend
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
