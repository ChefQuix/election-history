<template>
    <div>
        <a v-for="year in years" :key="year" 
        @hover="selectYear(year)" 
        @click="selectYear(year)">{{ year }}</a>
    </div>
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