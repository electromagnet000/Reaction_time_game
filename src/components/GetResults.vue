<template>
  <p>Reaction time : {{ score }} ms</p>
  <p class="rank"> {{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data() {
      return {
        rank: null,
      }
    },
    mounted() {
      if (this.score < 100) {
        this.rank = 'You are A GOD'
      } else if (this.score < 200){
        this.rank = "You're the reason your team won"
      } else if (this.score < 400) {
        this.rank = "You're the reason your team lost"
      } else {
        this.rank = 'that was shit Kill Yourself'
      }
    }
}
</script>

<style>
  .rank{
    font-size: 30px;
    color: blue;
    font-weight: bold;

  }
</style>