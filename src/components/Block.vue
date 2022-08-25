<template>
  <div class="block" v-show="showBlock" @click="stopTimer">click me</div>
</template>

<script>
export default {
  name: "Block",
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    console.log("mounted");
    console.log("delay", this.delay);
    setTimeout(() => {
      console.log("start time out");
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      console.log("startTimer");
      this.timer = setInterval(() => {
        this.reactionTime += 1;
      }, 10);
    },
    stopTimer() {
      // stop the timer
      clearInterval(this.timer);
      console.log(this.reactionTime);
      this.$emit("end", this.reactionTime);
    },
  },
  updated() {
    console.log("updated block");
  },
  unmounted() {
    console.log("unmounted");
  },
};
</script>

<style scoped>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
