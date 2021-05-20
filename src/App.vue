<template>
  <div id="nav">
    <h1>Reaction Score <br>Game</h1>
    <button id="play" @click="startGame" :disabled="isPlaying">play</button>
    <button id="restart" @click="restart">Restart</button>
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
    },
    restart(){
      window.location.reload()
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
  h1{
    text-transform: uppercase;
  }
  button{
    background: transparent;
    border: 1px solid #333;
    padding: 10px 30px;
    cursor: pointer;
    margin: 10px;
    font-weight: bold;
    text-transform: uppercase;
  }
  #play{
    &:hover{
      background: green;
      color: white;
    }
  }
  #restart{
    &:hover{
      background: red;
      color: white;
    }
  }
}
</style>
