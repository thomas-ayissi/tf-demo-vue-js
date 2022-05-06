<script lang="ts">
import NavBar from "./components/NavigationBar.vue"
export default {
  components : {
    NavBar
  }
}
</script>

<template>
  <NavBar></NavBar>

  <main>
    <RouterView/>
  </main>

  
</template>

<style>

</style>