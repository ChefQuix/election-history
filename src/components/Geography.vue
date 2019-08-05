<template>
<span>
    <img :src="current_file" height="550px">
</span>
</template>

<script>
export default {
    props: ['type', 'year'],
    data() {
        return {
        }
    },

    computed: {
        current_file() {
            return require('@/assets/Manitoba-' + this.year + '-' + this.type + '.png');
        }
    }


}
</script>

<style>
@media only screen and (max-width: 485px) {
    img {
        width: 100%;
        height: auto;
    }
}

</style>