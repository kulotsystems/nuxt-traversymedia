<template>
    <div v-if="joke">
        <nuxt-link to="/jokes" style="margin-bottom: 30px;">Back to Jokes</nuxt-link>
        <h2>{{ joke.joke }}</h2>
        <hr>
        <small><code>Joke ID: {{ joke.id }}</code></small>
    </div>
</template>

<script>

    export default {
        name: 'SingleJoke',
        data() {
            return {
                joke: {}
            }
        },
        async created() {
            const config = {
                headers: {
                    'Accept': 'application/json'
                }
            }
            try {
                const res = await this.$axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config);
                this.joke = res.data;
            }
            catch(err) {
                console.log('ERROR: ', err);
            }
        },
        head() {
            return {
                title: 'Joke' + (this.joke.id ? ' ' + this.joke.id : ''),
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
