<template>
  <h1>app component</h1>
  <br>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResults" :score="score"/>
</template>

<script>
import Block from './components/block'
import Results from './components/results.vue'
export default {
  name: 'App',
  components: {
  Block,
  Results
  },
  data(){
    return{
      isPlaying:false,
      delay:null,
      score:null,
      showResults:false
    }
  },
  methods:{
    start(){
      this.delay=2000+Math.random()*5000,
      this.isPlaying=true,
      this.showResults=false,
      console.log(this.delay)
    },
    endGame(reactionTime){
      this.score=reactionTime,
      this.isPlaying=false,
      this.showResults=true
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
  color: #2c3e50;
  margin-top: 60px;
}
button{
  background-color: seagreen;
  color: #fff;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
}
button[disabled]{
  cursor:not-allowed;
  opacity: 0.6;
}
</style>
