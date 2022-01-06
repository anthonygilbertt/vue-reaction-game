<template>
  <h1>Vue Reaction Game</h1>
  <button @click="start" :disabled="isPlaying">Play</button> |
  <button @click="refreshPage">Play again</button>

  <Results v-bind:score="score" />
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />

  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
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
    refreshPage() {
      location.reload();
    },
  },
};
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
html {
  background-color: pink;
  background-image: url("https://media.giphy.com/media/zW0n7AIWG4ka4/giphy.gif");
  background-repeat: repeat;
  background-size: cover;
  background-size: 100%;
}
h1,
p {
  color: aqua;
}
</style>
