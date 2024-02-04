<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" v-bind:disabled="isPlaying">play</button>
  <Block v-if="isPlaying" v-bind:delay="delay" @end="endGame" />
  <!-- <p v-if="showResults">Reaction time: {{ score }}</p> -->
  <Result v-if="showResults" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: { Block, Result },
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
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
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
</style>
