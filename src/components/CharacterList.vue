<template>
    <ul class="collection">
      <li class="collection-item avatar" v-for="(character,index) in characters" :key="index">
        <img src="https://cdn.iconscout.com/icon/free/png-256/avatar-372-456324.png" class="circle"
        />
        <span class="title">{{character.name}}</span>
        <a id="detail" href="javascript:void(0)" v-if="!checks[index]" v-on:click="changeChecks(index)"><br><br>Show Details</a>
          <template v-if="checks[index]">
            <p>Gender : {{character.gender}}</p>
            <p>Hair Color : {{character.hair_color}}</p>
            <p>Eye Color : {{character.eye_color}}</p>
            <p>Height : {{character.height}}</p>
            <p>Mass : {{character.mass}}</p>
          </template>
        <a href="javascript:void(0)" v-if="checks[index]" v-on:click="changeChecks(index)">Hide Details</a>
      </li>
    </ul>
</template>

<script>
export default {
  props: {
    characters: Array
  },
  data(){
    return{
      checks: []
    }
  },
  methods:{
    changeChecks(index){
      this.$set(this.checks, index, !this.checks[index]);
    },
    initChecks(){
      let i;
      for (i=0;i<this.characters.length;i++){
        this.checks[i] = false;
      }
    },
    addChecks(){
      this.checks.push(false);
      }
  },
  created(){
      this.initChecks()
  }
};
</script>

<style>
 ul{
        border: none;
    }
</style>
