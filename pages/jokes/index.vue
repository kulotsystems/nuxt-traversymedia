<template>
    <div>
        <JokeSearch @searchJoke="searchJoke"/>
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
    import JokeSearch from '../../components/JokeSearch.vue';

    export default {
        name: 'Jokes.Index',
        components: {
            Joke,
            JokeSearch
        },
        data() {
            return {
                jokes: []
            }
        },
        methods: {
            async searchJoke(text) {
                const config = {
                    headers: {
                        'Accept': 'application/json'
                    }
                }
                try {
                    const res = await this.$axios.get(`https://icanhazdadjoke.com/search?term=${text}`, config);
                    this.jokes = res.data.results;
                }
                catch(err) {
                    console.log('ERROR: ', err);
                }
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
