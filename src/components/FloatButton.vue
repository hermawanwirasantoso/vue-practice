<template>
<div>
  <div class="fixed-action-btn">
    <a class="btn-floating btn-large green" @click="getCharacters">
      <i class="large material-icons">add</i>
    </a>
  </div>
</div>
</template>


<script>
import axios from "axios";
export default {
  data() {
    return {
      characters: [],
      index: 0
    };
  },
  methods: {
    getCharacters() {
      axios
        .get("https://swapi.co/api/people/" + ++this.index)
        .then(response => {
          // handle success
          // console.log(response);
          this.characters.push(response.data);

          this.$emit("character-added", this.characters);
          console.log(this.characters);
        })
        .catch(error => {
          // handle error
          console.log(error);
        })
        .then(() => {
          // always executed
        });
    }
  }
};
</script>

<style>
</style>
