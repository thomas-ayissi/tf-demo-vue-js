<template>
  <div class="chapter">
    <h2>Exercice Timer</h2>
    <div>{{time}}</div>
    <button class="btn" @click="start()" :disabled="timer!=0">Start</button>
    <button class="btn" @click="pause()" :disabled="timer==0">Pause</button>
    <button class="btn" @click="reset()" :disabled="secondes==0">Reset</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent ({
  name: "Test",
  created() {},
  data() {
    return {
      secondes : 0,
      timer : 0,
    };
  },
  computed: {
    time() : string {
      let min = Math.floor(this.secondes/60);
      let sec = this.secondes % 60;
      let heu = Math.floor(min/60);
      min = min%60;
      return `${(heu > 9 ? heu : '0'+heu)} : ${min > 9 ? min : '0'+min} : ${sec > 9 ? sec : '0'+sec}`;
    }
  },
  methods: {
    start() : void {
      this.timer = setInterval(() => { this.secondes ++ }, 1000);
    },
    pause() : void {
      clearInterval(this.timer);
      this.timer = 0;
    },
    reset() : void {
      this.secondes = 0;
      this.pause();
    },
  },
});
</script>

<style lang="scss" scoped></style>