<template>
  <div  class="home ">
 
    
    <div class="flex justify-center mb-10" >
       <h1 class="p-5 bg-green-400 rounded w-1/3" >Quick reaction Game</h1>

    </div>
     <p  >How fast can you react ?</p>

     <button @click="start" :class="{ hidden: isplaying }"  class="p-2 rounded text-black border border-gray-400" >Start Game</button>
     <p v-if="gamestart" > Get ready to react !! </p>
     <Quick v-if="showquick"  :delay="delay" @end="showResult" />

     <div v-if="showRe" > 
        <p> clicked in  {{ score/1000}} seconds </p>

        <p class="my-5" > {{ word }} </p>
       <button @click="again" > Play again? </button>
     </div>
     
  </div>
</template>

<script>
// @ is an alias to /src
import Quick from '@/components/Quick.vue'

export default {
  name: 'HomeView',
  components: {
    Quick
  },
  data(){
    return{
      isplaying: false,
      showquick:false,
      delay: '',
      showRe: false,
      score : null,
      gamestart : false,
      word: ''

    }
  },
  methods:{
    start(){
      this.gamestart =true,
      this.delay = 2000 + Math.random() * 5000 ;
      console.log(this.delay);
      this.showquick= true ;
      this.isplaying = true;
    },
    showResult(reaction){
      this.showRe = true
      this.gamestart =false
      this.score = reaction
      this.showquick = false;
      if ( 0.1 > this.score/1000 ) {
        this.word = "send aza🤞🐱‍👤"
      }
      else if ( 0.3 >  this.score/1000 > 0.1 ) {
        this.word = 'great reflexxxxx😎'
      } else if( 0.6 >  this.score/1000 > 0.3) {
        this.word = 'niceee attempt🙌'
      }else if(  1 >  this.score/1000 > 0.6) {
        this.word = ' niceee but you can do better👍'
      }else if( 2 >  this.score/1000 > 1) {
        this.word = 'snail attempt'
      }else{
        this.word = 'you need to probably meet flash to teach you some moves 😂👍'
      }
    },
    again(){
       this.delay = 2000 + Math.random() * 5000 ;
     
      this.showquick= true ;
      this.gamestart =true;
      this.isplaying = true;
       this.showRe = false
    }
     
  }
 
}
</script>
