<template>
    <div>
        <Joke
            v-for="joke in jokes"
            :key="joke.id"
            :joke="joke.joke"
            :id="joke.id"
        />
    </div>
</template>

<script>
    import Joke from '../../components/Joke.vue';

    export default {
        name: 'Jokes.Index',
        components: {
            Joke
        },
        data() {
            return {
                jokes: []
            }
        },
        async created() {
            const config = {
                headers: {
                    'Accept': 'application/json'
                }
            }
            try {
                const res = await this.$axios.get('https://icanhazdadjoke.com/search', config);
                this.jokes = res.data.results;
            }
            catch(err) {
               console.log('ERROR: ', err);
            }
        },
        head() {
            return {
                title: 'Dad Jokes',
                meta : [
                    {
                        hid    : 'description',
                        name   : 'description',
                        content: 'Best place for corny dad jokes'
                    }
                ]
            }
        }
    }
</script>

<style scoped>

</style>
