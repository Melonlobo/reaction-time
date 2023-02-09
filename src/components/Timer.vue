<template>
  <div class="block" @click="getReactionTime">CLICK ME!</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    console.log("mounted in ", this.delay);
    this.timer = setInterval(() => {
      this.reactionTime += 10;
    }, 10);
  },
  unmounted() {
    console.log("unmounted");
  },
  methods: {
    getReactionTime() {
      this.$emit("end", this.reactionTime);
      clearInterval(this.timer);
      this.reactionTime = 0;
    },
  },
};
</script>

<style>
.block {
  margin: 100px auto;
  background: #f00;
  color: #fff;
  width: 10rem;
  height: 10rem;
  border-radius: 0.3rem;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
