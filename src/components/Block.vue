<template lang="ts">
    <div class = "block"  @click='stopTimer' v-if = 'showBlock'>
        click me
    </div>
</template>
<script lang = "ts">
export default {
    props: ['delay'],
    data() {
        return {
            showBlock : false,
            timer: 0,
            reactionTime: 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.startTimer();
            this.showBlock = true;
        }, this.delay);
    },
    methods: {
        startTimer(){
                  this.timer = setInterval(() => {
                    this.reactionTime = this.reactionTime + 10;
            }, 10);
        },
        stopTimer(){
            clearInterval(this.timer);
            console.log(this.reactionTime);
            this.$emit('end', this.reactionTime);
        },
    },
    
}
</script>
<style>
.block {
    background-color: aquamarine;
    color: rgb(0, 0, 0);
    text-align: center;
    width: 400px;
    border-radius: 25px;
    padding: 100px 0;
    margin: 50px auto;
}
    
</style>