<template>
      <p>Reaction Time: {{ score }} ms</p>
      <p class="rank"> {{ rank }}</p>
</template>

<script>
export default {
    props: ["score"],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 250) {
            this.rank = "Ninja Fingers"
        } else if (this.score < 400) {
            this.rank = "Rapid Reflexes"
        } else {
            this.rank = "Snail pace"
        }
    }
}
</script>

<style>
    p {
        color: red;
    }
    .rank {
        font-size: 1.3rem;
        color: rgb(7, 5, 5);
        font-style: italic;
    }
</style>