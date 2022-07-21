<template>
    <form @submit.prevent="searchJoke">
        <input type="text" v-model="text" placeholder="Search Jokes...">
        <input type="submit" value="Search Jokes">
    </form>
</template>

<script>
    export default {
        name: 'JokeSearch',
        data() {
            return {
                text: ''
            }
        },
        methods: {
            searchJoke() {
                this.$emit('search-joke', this.text);
                this.text = '';
            }
        }
    }
</script>

<style scoped>

</style>
