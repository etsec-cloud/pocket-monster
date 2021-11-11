<template>
  <div>
    <div>
      {{ pokemonInfo.name }}
    </div>
    <div v-for="type in pokemonInfo.types" :key="type.id">
      {{ type.type.name }}
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    pokemon: {},
  },
  data() {
    return {
      pokemonInfo: {},
      types: [],
    };
  },
  mounted() {
    this.fetchInfoPokemon();
  },
  methods: {
    fetchInfoPokemon: function () {
      const baseURI = this.pokemon.url;
      this.$http.get(baseURI).then(result => {
        this.pokemonInfo = result.data;
        console.log(this.pokemonInfo);
      });
      this.types = this.pokemonInfo.type;
    },
  },
};
</script>

<style></style>
