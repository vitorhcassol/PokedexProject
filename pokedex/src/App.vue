<template>
  <div>
    {{queryAtual}}
  </div>
</template>

<script>


export default {
  name: 'App',
  
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
