<template>
    <ul>
        <li>Election</li>
        <li v-for="year in years" :key="year">
            <a @mouseover="selectYear(year)" 
                @click="selectYear(year)" 
                class="year" :class="{ 'font-weight-black': year==current_year}">{{ year }}</a>
            </li>
    </ul>
</template>

<script>
export default {
    data() {
        return {
            current_year: 0,
        }
    },
    props: {years: Array},
    methods: {
        selectYear(year) {
            this.$emit('select-year',year);
            this.current_year = year;
        }
    },
    created() {
        if (this.years.length) {
            this.current_year = this.years[0];
        }
    },
    watch: {
        years(to,from) {
            if ((from.length === 0) && (to.length !== 0)) {
                this.current_year = to[0];
            }
        }
    }
}
</script>
<style>
ul { list-style: none; }
li .year:hover { cursor: pointer; }
</style>