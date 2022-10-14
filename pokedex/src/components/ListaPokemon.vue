<template>
    <section v-for="pokemon in this.lista"
    :key="pokemon.name"
    class="list">
        <Card :pokemonURL="pokemon.url"></Card>
    </section>
</template>

<script>

    import Card from './Card.vue';

export default {
    props: ["queryAtual"],
    components: {
        Card
    },

    data() {
        return {
            lista: undefined
        };
    },
    methods: {
        getLista(queryAtual) {
            this.axios
            .get(queryAtual)
            .then((response) => {
                this.lista = response.data.results;
            });
        }
    },
    created() {
        this.getLista(this.queryAtual);
    },
    updated() {
        this.getLista(this.queryAtual);
    }
}

</script>

<style scoped>
    .list {
        padding: 3.2rem 2.4rem 2.4rem 2.4rem;
    }
</style>