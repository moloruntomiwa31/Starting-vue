<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click me
    </div>
</template>

<script>
export default {
    props: ["delay"],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        setTimeout(( ) => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10);
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit("end", this.reactionTime)
        }
    }
}
</script>

<style>
    .block {
        max-width: 300px;
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 10px;
        color: white;
        background-color: #004e00;
        border-radius: 15px;
        margin: 30px auto;
        height: 100px;
        cursor: pointer;
    }
</style>