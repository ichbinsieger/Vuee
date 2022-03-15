<template>
  <div class="hello w-full flex justify-center"  v-if="showblock"  >
    <div @click="stopTimer"  class="bg-slate-500 mt-20  h-40  flex justify-center items-center rounded-md w-1/2 " >
    <h1> Click me asap!!!! </h1>
    </div>
  </div>
</template>

<script>
export default {
  name: 'QuickReact',
  props:["delay"],
 
  data(){
    return{
      showblock: false,
       timer: null,
       reactTime: 0
    }
  },
   mounted(){
    setTimeout(() => {
      this.showblock = true;
      this.startTimee();
      console.log(this.timer);
     
      
    }, this.delay);
    

  },
  methods:{
    startTimee(){
      
        this.timer = setInterval(() => {
          this.reactTime += 10
        }, 10);
      
    },
    stopTimer(){
     clearInterval(this.timer)
      console.log(this.reactTime);
      this.$emit('end',this.reactTime)
    },

  }


 
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
