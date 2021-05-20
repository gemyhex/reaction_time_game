<template>
  <div id="nav">
    <h1>Reaction Time</h1>
    <button @click="startGame" :disabled="isPlaying">play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
    <Results v-if="showResults" :score="score"></Results>
  </div>
  <router-view />
</template>

<script>
import Block from "./components/Block"
import Results from "./components/Results"
export default {
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  components:{
    Block,
    Results
  },
  methods: {
    startGame(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
    },
    endGame(reactionTime){
      this.score = reactionTime;
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>


<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
