<template>
    <h1>My reaction timer</h1>
    <button @click="start" :disabled='isPlaying'>Play</button>
    <BlockVue v-if="isPlaying" :delay="delay" @end="endGame"/>
    <ResultsVue v-if="showResults" :reactionTime="reactionTime"/>
</template>

<script>
import BlockVue from './components/Block.vue';
import ResultsVue from './components/Results.vue';

export default {
    name: 'App',
    components: {BlockVue, ResultsVue},
    data() {
        return {
            isPlaying: false,
            delay: null,
            reactionTime: null,
            showResults: false,
        }
    },
    methods: {
        start() {
            this.delay = 2000 + Math.random() * 5000;
            this.isPlaying = true;
            this.showResults = false;
        },
        endGame(reactionTime) {
            this.reactionTime = reactionTime;
            this.isPlaying = false;
            this.showResults = true;
        },
    }
}
</script>

<style>
#app {
    font-family: Arial, Helvetica, sans-serif;
    text-align: center;
    color: #444;
    margin-top: 60px;
}

button {
    background: #0faf87;
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    font-size: 16px;
    letter-spacing: 1px;
    cursor: pointer;
    margin: 10px;
}

button[disabled] {
    opacity: 0.2;
    cursor: not-allowed;
}
</style>