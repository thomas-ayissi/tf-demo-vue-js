

<script lang="ts">
import { defineComponent } from "vue"
export default defineComponent ({
  name: "Card",
  data() {
    return {};
  },
  props: {
    lastname : String,
    firstname : String,
    birthdate : String,
  },
  emits : [
    'who'
  ],
  methods : {

  }
})
</script>

<template>
  <div class="card">
    <div class="fullname">{{firstname}} {{lastname}}</div>
    <div>{{birthdate}}</div>
    <slot></slot>
    <button @click="$emit('who', firstname)">C'est moi</button>
  </div>
</template>

<style>
.card {
  background-color: lightblue;
  width: 200px;
  height: 200px;
  margin: 1%;
}
.fullname {
  font-weight: bold;
}
</style>