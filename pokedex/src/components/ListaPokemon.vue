<template>
    <section v-for="pokemon in this.lista" :key="pokemon.name">
        {{ pokemon.name }}
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
    },

    updated() {
        this.getLista(this.queryAtual)
    }
}

</script>

<style scoped>

</style>