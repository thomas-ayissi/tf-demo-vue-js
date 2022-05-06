<template>
  <div class="chapter">
    <h2>Les bindings</h2>
    <div class="demoflex">
      <div class="democard">
        <h3 class="democardtitle">Property binding</h3>
        <div class="subchapter">
          <h4>Binding One-Way</h4>
          <div>Bienvenue {{ prenom }}</div>
        </div>
        <div class="subchapter">
          <h4>Binding Two-Way</h4>
          <div>Votre prénom est {{ prenom }}</div>
          <input type="text" v-model="prenom" />
        </div>
        <div class="subchapter">
          <h4>Binding HTML</h4>
          <div>{{ duHTML }}</div>
          <div v-html="duHTML"></div>
        </div>
      </div>

      <div class="democard">
        <!-- Event binding -->
        <h3 class="democardtitle">Event Binding</h3>
        <div class="subchapter">
          <button class="btn" v-on:click="sayHello()">Say Hello</button>
          <!-- Le raccourcis que tout le monde utilise :  -->
          <button class="btn" @click="sayHello()">Say Hello</button>
          <div>{{ message }} {{ prenom }}</div>
        </div>

      </div>

      <div class="democard">
        <!-- Attribute binding -->
        <h3 class="democardtitle">Attribute Binding</h3>
        <div v-bind:id="id">Ma div avec plein d'attributs</div>
        <button class="btn" v-bind:disabled="isInactive">Click</button>
        <!-- Avec le raccourcis que tout le monde utilise :) -->
        <div :id="id" :class="maClass">Ma div avec plein d'attributs</div>
        <button class="btn" :disabled="isInactive">Click</button>
      </div>

      <div class="democard">
        <h3 class="democardtitle">Computed properties</h3>
        <label for="lastname">Nom de famille</label>
        <input id="lastname" type="text" v-model="lastname">
        <label for="firstname">Prénom</label>
        <input id="firstname" type="text" v-model="firstname">
        <div>Bienvenue {{ fullname }} ! </div>
      </div>

    </div>

  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "DemoBinding",
  created() { },
  data() {
    return {
      prenom: "Aude",
      duHTML: "<p>Mon paragraphe</p>",
      message: "Bonjour",
      id: "monId",
      isInactive: true,
      maClass: "green",
      lastname: "",
      firstname: "",
    };
  },
  computed: {
    fullname(): string {
      return `${this.firstname} ${this.lastname}`
    }
  },
  methods: {
    sayHello(): void {
      this.message = "Hello";
    },
  },
});
</script>

<style lang="scss" scoped>
</style>