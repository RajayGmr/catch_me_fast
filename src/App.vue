<template>
  <h1>How Fast Can you catch me?</h1>
  <h2>คุณจับฉันได้เร็วแค่ไหน?</h2>
  <button @click="start" :disabled="isPlaying">Play / เล่น</button>
  <div v-if="isPlaying">
    <blockCom :delay="delay" @endGame="EndGame"></blockCom>
    <!-- <p>Result is - {{score}}ms</p> -->
  </div>
  <div v-if="end">
    <resultCom :gamescore="score"></resultCom>
  </div>
  
  
</template>

<script>
import Block_Com from "./components/Block.vue"
import Result_Com from "./components/Result.vue"

export default {
  name: 'App',
  components: {
    blockCom:Block_Com,
    resultCom:Result_Com
    
  },
  data(){
    return{
      isPlaying: false,
      delay: null,
      score:0,
      end:false,
    }
  },
  methods:{
    start(){
      this.isPlaying=true;
      this.delay=2000+Math.random()*5000;
      
    },
    EndGame(score){
      this.score=score;
      this.isPlaying=false;
      this.end=true;
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
</style>
