<template>
    <div>
        jokes
    </div>
</template>

<script>
    export default {
        name: 'Jokes.Index',
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
