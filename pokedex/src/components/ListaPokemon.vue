<template>
    <section v-for="index in this.lista">
        {{ index.name }}
    </section>
</template>

<script>

export default {
    props: ['queryAtual'],

    data() {
        return {
            lista: undefined
        }
    },

    methods: {
        getLista(queryAtual) {
            this.axios
            .get(queryAtual)
            .then((response) => {
                this.lista = response.data.results;
            })
        }
    },

    created() {
        this.getLista(this.queryAtual)
    }
}

</script>

<style scoped>

</style>