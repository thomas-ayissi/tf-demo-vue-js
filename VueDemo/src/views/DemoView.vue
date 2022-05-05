<script lang="ts">
import { defineComponent } from "vue";
  export default defineComponent ({
    data() {
      return {
        prenom : "Aude",
        duHTML : "<p>Mon paragraphe</p>",
        message : "Bonjour",
        id : "monId",
        isInactive : true,
        maClass : "green",

        lastname : "",
        firstname : "",
      }
    },
    computed : {
      fullname() : string {
        return `${this.firstname} ${this.lastname}`
      }

    },
    methods : {
      sayHello() : void {
        this.message = "Hello";
      }

    }
  })
</script>

<template>
  <h1>Demo VueJS</h1>
  <!-- Binding one-way -->
  <h2>Binding One-Way</h2>
  <div>Bienvenue {{prenom}}</div>
  <!-- Binding two-way -->
  <h2>Binding Two-Way</h2>
  <input type="text" v-model="prenom">
  <!-- Binding avec du html : peu utilisé  -->
  <h2>Binding HTML</h2>
  <div v-html="duHTML"></div>

  <!-- Event binding -->
  <h2>Event Binding</h2>
  <button v-on:click="sayHello()">Say Hello</button>
  <!-- Le raccourcis que tout le monde utilise :  -->
  <button @click="sayHello()">Say Hello</button>
  <div>{{message}} {{prenom}}</div>

  <!-- Attribute binding -->
  <h2>Attribute Binding</h2>
  <div v-bind:id="id">Ma div avec plein d'attributs</div>
  <button v-bind:disabled="isInactive">Click</button>
  <!-- Avec le raccourcis que tout le monde utilise :) -->
  <div :id="id" :class="maClass">Ma div avec plein d'attributs</div>
  <button :disabled="isInactive">Click</button>

  <!-- Computed properties-->
  <label for="lastname">Nom de famille</label>
  <input id="lastname" type="text" v-model="lastname">
  <label for="firstname">Prénom</label>
  <input id="firstname" type="text" v-model="firstname">
  <div>Bienvenue {{fullname}} ! </div>
  <h2></h2>

</template>

<style>
.green {
  color : green;
}
</style>