<template>
  <div class="stopwatch-widget">
    <h2>Stopwatch</h2>
    <div>{{ formatTime }}</div>
    <div>
      <button @click="startStopwatch" v-if="!isRunning">Start</button>
      <button @click="stopStopwatch" v-else>Stop</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      startTime: null,
      elapsedTime: 0,
      timer: null,
      isRunning: false,
    };
  },
  computed: {
    formatTime() {
      const seconds = Math.floor(this.elapsedTime / 1000);
      const minutes = Math.floor(seconds / 60);
      const hours = Math.floor(minutes / 60);

      return `${this.pad(hours)}:${this.pad(minutes % 60)}:${this.pad(
        seconds % 60
      )}`;
    },
  },
  methods: {
    startStopwatch() {
      this.startTime = Date.now() - this.elapsedTime;
      this.timer = setInterval(() => {
        this.elapsedTime = Date.now() - this.startTime;
      }, 10);
      this.isRunning = true;
    },
    stopStopwatch() {
      clearInterval(this.timer);
      this.isRunning = false;
    },
    pad(number) {
      return number.toString().padStart(2, '0');
    },
  },
};
</script>

<style scoped>
.stopwatch-widget {
  text-align: center;
  margin-top: 20px;
}
</style>
