<template>
  <div id="app">
    <div class="mb-3">
      <h3 class="fs-1 fw-bold">Reaction Timer</h3>
      <p class="fs-5">Test your reaction times</p>
      <button class="btn btn-success" @click="playGame" :disabled="isPlaying">Get Started</button>
    </div>
      <Blocks v-if="isPlaying" :delay="delay" @end="endGame"/>
    
    <Results v-if="played" :score="score" />
  </div>
</template>

<script>
import Blocks from "./components/Blocks.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      played: false,
    };
  },
  methods: {
    playGame(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
    },
    endGame(reactionTime){
      // console.log(reactionTime)
      this.played = true,
      this.score = reactionTime
    } 
  },
  components: {
    Blocks,
    Results,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
