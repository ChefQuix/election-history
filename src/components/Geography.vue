<template>
<span>
    <img :src="current_file">
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