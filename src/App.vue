<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <Block v-if=isPlaying :delay="delay" @end="endGame"/>
  <Results v-if="showResults" :score="score"/>
</template>

<script>

import Block from "./components/Block.vue"
import Results from "./components/Results.vue"

export default {
  name: 'App',
  data() {
    return {
        isPlaying: false,
        delay: null,
        score: null,
        showResults: false
    }
  },
  components: { Block, Results },
  methods: {
    start() {
      this.isPlaying = true,
      this.delay = 2000 + (Math.random() * 5000)
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>

<style>
#app {
  font-family: Poppins, Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #221f1f;
  margin-top: 60px;
}
button {
  border: none;
  padding: 10px;
  background-color: green;
  color: white;
  cursor: pointer;
  border-radius: 4px;
  font-family: Syne;
}
</style>
