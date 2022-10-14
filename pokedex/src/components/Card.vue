<template>
    <div id="card">
        <div class="col-a">
            <p> {{ this.name }} </p>

            <div v-for="tipo in this.types"
            :key="tipo.index">
                <div class="type">
                    {{ tipo.type.name }}
                </div>
            </div>

            <span> #{{ this.id }} </span>
        </div>

        <div class="col-b">
            <img :src="image" alt="">
        </div>
    </div>
</template>

<script>

export default {
    props: ["pokemonURL"],
    data() {
        return {
            id: undefined,
            name: undefined,
            types: undefined,
            image: undefined
        }
    },

    methods: {
        getPokemonInfo(pokemonURL) {
            this.axios
            .get(pokemonURL)
            .then((response) => {
                this.id = response.data.id;
                this.name = response.data.name;
                this.types = response.data.types;
                this.image = response.data.sprites.front_default;
            })
        }
    },

    created() {
        this.getPokemonInfo(this.pokemonURL);
    },
    updated() {
        this.getPokemonInfo(this.pokemonURL);
    }
}

</script>

<style scoped>
    #card {
        display: grid;
        grid-template-columns: 40% 1fr;
        grid-template-areas:
        'A B';

        width: 15rem;
        height: 11rem;
        border-radius: 1.5rem;

        padding: 1.6rem 1.6rem 1rem 1.6rem;

        background-color: var(--secondary-color);

        box-shadow: 0.2rem 0.2rem var(--aux-black);

        font-family: 'VT323', monospace;
        font-size: 1.6rem;
        color: white;
    }

    .col-a {
        grid-area: A;
    }

    .col-b {
        grid-area: B;
    }

    .type {
        display: inline;
        border-radius: 2rem;

        padding: 0.2rem 0.8rem;

        background-color: var(--aux-black-2);

        font-size: 1.2rem;
    }
</style>