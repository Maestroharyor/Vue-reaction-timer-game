<template >
    <div class="bg-success click_board mx-auto rounded text-white fs-3 mb-5 d-flex justify-content-center align-items-center" v-if="showBlock" @click="stopTimer">
      <p>Click Me</p>
    </div>
</template>


<script>
export default {
  name: "blocks-component",
  props: ['delay'],
  data(){
    return{
      showBlock: false,
      timer: null,
      reactionTime: 0
    }
  },
  methods: {
    startTimer(){
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10);
    },
    stopTimer(){
      this.showBlock = false,
      clearInterval(this.timer)
      this.$emit('end', this.reactionTime)
    }
  },
  mounted(){
    // console.log("Mounted")
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
      // console.log(this.delay)
    }, this.delay);
  }
};

</script>


<style>
  .click_board{
    width: 250px;
    height: 200px;
  }
</style>