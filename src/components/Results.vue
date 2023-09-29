<template>
  <div>
    <p class="description">Your reaction time is: <span class="time">{{ reactionTime }} ms</span></p>
    <span class="rank">{{ rank }}</span>
  </div>
</template>

<script>
export default {
  props: ["reactionTime"],
  data() {
    return {
        rank: null,
    }
  },
  mounted() {
    if (this.reactionTime < 200) {
        this.rank = 'Pro';
    } else if (this.reactionTime < 300) {
        this.rank = 'Mid';
    } else {
        this.rank = 'Noob';
    };
  }
};
</script>

<style>
.description {
    font-size: 1em;
    color: black;
    font-weight: bold;
}

.time {
    font-size: 1em;
    color: red;
    font-weight: bold;
}

.rank {
    font-size: 1em;
    color: #0faf87;
    font-weight: bold;
}
</style>