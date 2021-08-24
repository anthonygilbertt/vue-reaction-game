<template>
  <h1>Vue Ninja Reaction Game</h1>
  
    <h3 v-if="showResults">this.reactionTime: {{this.reactionTime}} ms</h3>

  
  <button @click="start" :disabled="isPlaying">Play</button> | 
  <button @click="refreshPage">Play again</button>
  <Block v-if="isPlaying" v-bind:delay="delay" @end="endGame"/>
  <!-- <Results /> -->
</template>

<script>
import Block from './components/Block.vue'
// import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block,
    // Results
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
      
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },

    endGame(reactionTime) {
      this.score = this.reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
    refreshPage(){
      location.reload();
    }
  }
}


</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
