<script lang="ts">
import DemoBinding from "../components/DemoBinding.vue";
import DemoDirectives from "../components/DemoDirectives.vue";
import DemoComponent from "../components/DemoComponent.vue";
import { defineComponent } from "vue"
  export default defineComponent ({
    components : {
      DemoBinding,
      DemoDirectives,
      DemoComponent
    },
    data() {
      return {
      }
    },
    computed : {

    },
    methods : {
      

    }
  })
</script>

<template>
  <h1>Demo VueJS</h1>
  <DemoBinding></DemoBinding>
  <DemoDirectives></DemoDirectives>
  <DemoComponent></DemoComponent>

</template>

<style>
.green {
  color : green;
}
.bold {
  font-weight: bold;
}
.giant {
  font-size: 32px;
}
.flex {
  display: flex;
  justify-content: space-around;
}
</style>