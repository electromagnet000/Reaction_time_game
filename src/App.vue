<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <BlockReaction v-if="isPlaying" :delay="delay" @end="endGame"/>
  <GetResults v-if="showResults" :score="score"/>
</template>

<script>
import BlockReaction from './components/BlockReaction.vue'
import GetResults from './components/GetResults.vue'

export default {
  name: 'App',
  components: { BlockReaction, GetResults },
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
      this.delay = 2000 + Math.random() * 2000 
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime,
      this.isPlaying = false
      this.showResults = true
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

button {
  background: #1e1e1e;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
}

button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>