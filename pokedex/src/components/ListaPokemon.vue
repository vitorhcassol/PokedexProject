<template>
    <section
    class="list">
        <Card v-for="pokemon in this.lista"
        :key="pokemon.name"
        :pokemonURL="pokemon.url"></Card>
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
        display: grid;
        grid-template-columns: 50% 50%;
        grid-template-areas:
        'A B';
        row-gap: 1.2rem;
        justify-items: center;

        padding: 3.2rem 0rem;
    }
</style>