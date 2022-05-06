<template>
  <nav class="nav">
    <ul>
      <li v-for="link in links">
        <RouterLink :to="link.url">{{link.name}}</RouterLink>
      </li>
    </ul>
  </nav>
</template>

<script lang="ts">
export default {
  name: "Test",
  created() {},
  data() {
    return {
      links : [
        { url : '/', name : "Accueil"},
        { url : '/demo', name : "Demos"},
        { url : '/exercice', name : "Exercices"}
      ]
    };
  },
  props: {},
  methods: {},
};
</script>

<style lang="scss" scoped></style>