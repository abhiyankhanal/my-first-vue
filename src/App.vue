<template>
 <h1>Reaction Timer</h1>
 <button @click = 'start' :disabled="play">play</button>
 <Block v-if="play" :delay='delay' @end="endGame" />
 <Score v-if='showScore' :score='score' />
</template>

<script>
import { defineComponent } from 'vue';
import Block from './components/Block.vue'
import Score from './components/Score.vue'

export default defineComponent({
  name: 'App',
  components: {
    Block,
    Score
  },
  data() {
    return {
      play: false,
      delay: 0,
      score: 0,
      showScore: false
    }
  },
  methods: {
    start(){
      this.showScore = false;
      this.play = true;
      this.delay = 2000 + Math.random() * 5000;
      console.log(this.delay);
    },
    endGame(reactionTime){
      this.score = reactionTime;
      this.play = false;
      this.showScore = true
      console.log(this.score);
    }
    
  },
});
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
