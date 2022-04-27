<template lang="">
    <div class="pt-4 pb-2 border">
        <p class="fs-5">Reaction time - {{score}}ms</p>
        <p class="fw-bold fs-3">{{ comment }}</p>
    </div>
</template>

<script>
export default {
    name:"vue-component",
    props: ['score'],
    data(){
        return{
           comment: null 
        }
        
    },
    methods: {
    },
    mounted(){
        console.log(this.score)
        if(this.score < 250){
            this.comment = "Fast Fingers"
        } else if (this.score < 400){
            this.comment = "Rapid Reflexes"
        } else{
            this.comment = "Slow..."
        }
    }
}
</script>

<style lang="">
    
</style>