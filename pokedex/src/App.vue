<template>
  <Header></Header>
  <ListaPokemon :queryAtual="this.queryAtual"></ListaPokemon>

  <div id="footer">
    <div class="rounded">
      <!-- Botão de voltar -->
      <button
      :disabled="!this.queryAnterior"
      @click="getPokemonPage(queryAnterior)">
      <img src="./img/Arrow-left.png" alt="seta para a esquerda">
      </button>
      <!-- Botão de avançar -->
      <button
      @click="getPokemonPage(queryProxima)">
      <img src="./img/Arrow-right.png" alt="seta para a direita">
      </button>
    </div>
  </div>
</template>

<script>

  import ListaPokemon from '@/components/ListaPokemon.vue'
  import Header from '@/components/Header.vue'

export default {
  name: 'App',
  components: {
    ListaPokemon,
    Header
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

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  :root {
    /* Colors */
    --primary-color: #DC092C;
    --secondary-color: #70C2F4;

    --white: #FFFFFF;

    --black: #01261F;
    --aux-black: #01282175;

    /* 1rem = 10px */
    font-size: 62.5%;
  }

  html {
    scroll-behavior: smooth;
  }

  html,
  body {
    width: 100%;
    height: 100%;
  }

  #footer {
    height: 10.8rem;

    background-color: var(--primary-color);
  }

  .rounded {
    display: flex;
    justify-content: space-between;
    align-items: center;

    padding: 3.4rem 2.4rem;

    max-width: 37.5rem;

    margin: auto;
  }

  button {
    width: 12rem;
    height: 4rem;

    border-radius: 0.5rem;

    box-shadow: 0.2rem 0.2rem 0.2rem var(--aux-black);

    background-color: var(--black);

    border: none;
  }

  button:disabled {
    background-color: var(--aux-black);
  }
</style>
