<script lang="ts">
import { defineComponent } from "vue";
import Timer from "../components/Timer.vue";
import ListeCourse from "../components/ListeCourse.vue";
export default defineComponent ({
  name: "Test",
  components : {
    Timer,
    ListeCourse
  },
  created() {},
  data() {
    return {
      
    };
  },
  computed : {
  },
  props: {},
  methods: {
    
  },
});
</script>

<template>
  <h1>Exercices :</h1>
  <Timer/>
  <ListeCourse></ListeCourse>

  <div>
    
  </div>
</template>

<style scoped>
 
</style>