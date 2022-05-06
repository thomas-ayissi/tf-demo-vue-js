

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
    avatar : String,
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
    <img class="avatar" :src="'../../src/assets/images/'+ avatar" :alt="'avatar de '+firstname">
    <div class="fullname">{{firstname}} {{lastname}}</div>
    <div>{{birthdate}}</div>
    <slot></slot>
    <button class="btn" @click="$emit('who', firstname)">C'est moi</button>
  </div>
</template>

<style>

</style>