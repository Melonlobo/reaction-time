<template>
  <h1>Check your reaction time</h1>
  <button class="btn" :disabled="disabled" @click="start">START</button>
  <Timer v-if="started" :delay="delay" @end="reset" />
  <Results v-if="show" :reactionTime="reactionTime" />
</template>

<script>
import Timer from "./components/Timer.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  components: {
    Timer,
    Results,
  },
  data() {
    return {
      started: false,
      disabled: false,
      delay: null,
      reactionTime: null,
      show: false,
    };
  },
  methods: {
    start() {
      this.show = false;
      this.disabled = true;
      this.delay = 1000 + Math.random() * 5000;
      setTimeout(() => {
        this.started = true;
      }, this.delay);
    },
    reset(reactionTime) {
      this.reactionTime = reactionTime;
      this.started = false;
      this.disabled = false;
      this.show = true;
    },
  },
  props: {},
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 100px;
}
.btn {
  margin: 2.5rem 0;
  padding: 0.5rem 2rem;
  background-color: #000;
  color: #fff;
  border-radius: 1000px;
}
.btn:hover {
  background-color: #fff;
  color: #000;
  cursor: pointer;
}
.btn:disabled {
  opacity: 0.4;
  cursor: not-allowed;
}
</style>
