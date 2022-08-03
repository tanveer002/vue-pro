<template>
    <h1>Timer Game for demo</h1>
    <button type="" @click="play()" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
    <Result v-if="showResult" :score="score"/>
    
</template>

<script>
  import Block from './components/Block.vue'
  import Result from './components/Result.vue'
  export default{
    name: 'App',
    components: { Block, Result },
    data(){
      return {
       isPlaying : false,
       delay : null,
       score: null,
       showResult: false
      }
    },
    methods: {
      play(){
        this.delay = 1000 + Math.random() * 5000
        this.isPlaying = true
        console.log(this.delay);
        this.score = 0
      },
      endGame(reactionTime){
        this.score = reactionTime
        console.log("your total score is",this.score)
        this.isPlaying = false
        this.showResult = true
      }
      }
  }
</script>

<style>
  #app{
    text-align:center;
    color:#444;
    margin-top:60px;
  }
</style>



