<template>
  <div class="block" v-if="showBlock" @click="stop">
      click me
  </div>
</template>

<script>
export default {
    data(){
        return {
            showBlock: false,
            timer: null,
            reactionTimer: 0
        }
    },
    props: ['delay'],
    mounted(){
        setTimeout(() => {
            this.showBlock = true
            this.start()
        } , this.delay)
    },
    methods: {
        start(){
            this.timer = setInterval(() => {
                this.reactionTimer += 10
            } , 10)
        },
        stop(){
            clearInterval(this.timer)
            this.$emit('end' , this.reactionTimer)
        }
    }
}
</script>

<style>
    .block{
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>