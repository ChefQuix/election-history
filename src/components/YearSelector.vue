<template>
    <ul>
        <li>Election</li>
        <li v-for="year in years" :key="year">
            <a @mouseover="selectYear(year)" 
                @click="selectYear(year)" 
                class="year">{{ year }}</a>
            </li>
    </ul>
</template>

<script>
export default {
    props: ['years'],
    methods: {
        selectYear(year) {
            this.$emit('select-year',year);

        }
    }
}
</script>
<style>
ul { list-style: none; }
li .year:hover { cursor: pointer; }
</style>