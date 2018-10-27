<template>
  <div id="app">
    <navbar-starwars v-model="parentValue" @input="filterCharacters"></navbar-starwars>
      <float-button @character-added="showCharacters"></float-button>
      <character-list :characters="characters" ref="cList"></character-list>
  </div>
</template>

<script>
import navbarStarwars from "./components/NavbarStarwars";
import floatButton from "./components/FloatButton";
import characterList from "./components/CharacterList";

export default {
  name: "App",
  components: {
    navbarStarwars,
    floatButton,
    characterList
  },
  data() {
    return {
      characters: [],
      a: [],
      parentValue: ""
    };
  },
  methods: {
    showCharacters(payload) {
      this.characters = payload;
      this.a = payload.slice();
      this.$refs.cList.addChecks();
    },
    filterCharacters() {
      this.characters = this.a.filter(character => {
        return character.name
          .toLowerCase()
          .includes(this.parentValue.toLowerCase());
      });
      if (this.parentValue.length <= 0) {
        this.characters = this.a;
      }
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100vh;
  position: relative;
}
</style>
