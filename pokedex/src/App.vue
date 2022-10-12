<template>
  <ListaPokemon :queryAtual="this.queryAtual"></ListaPokemon>

  <!-- Botão de voltar -->
  <button
  :disabled="!this.queryAnterior"
  @click="getPokemonPage(queryAnterior)"> \ </button>

  <!-- Botão de avançar -->
  <button
  @click="getPokemonPage(queryProxima)"> / </button>
</template>

<script>

  import ListaPokemon from '@/components/ListaPokemon.vue'

export default {
  name: 'App',
  components: {
    ListaPokemon
  },
  
  data() {
    return {
      queryAtual: undefined,
      queryProxima: undefined,
      queryAnterior: undefined
    }
  },
  
  methods: {
    getPokemonPage(query) {
      this.queryAtual = query;

      this.axios
      .get(query)
      .then((response) => {
        this.queryProxima = response.data.next;
        this.queryAnterior = response.data.previous;
      })
    }
  },

  created() {
    this.getPokemonPage("https://pokeapi.co/api/v2/pokemon?limit=10&offset=0")
  }

}

</script>

<style scoped>

</style>
