<script lang="ts">
import Card  from "../components/Card.vue";
import { defineComponent } from "vue"
// import Card from "../components/Card.Vue";
  export default defineComponent ({
    components : {
      Card,
    },
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

        isGreen : true,
        isBold : true,
        isGiant : true,

        fontSize : '24px',
        weight : 'bold',

        isVisible : true,

        formateurs : ['Khun', 'Steve', 'Aurélien', 'Loïc', 'Aude'],
        formateurDuJour : "",
        formateursBis : [
          { id : 0, lastname : "Ly" , firstname : "Khun" , birthdate : "06/05/1982"},
          { id : 1, lastname : "Strimelle", firstname : "Aurélien", birthdate : "01/11/1989"},
          { id : 2, lastname : "Beurive", firstname : "Aude", birthdate : "16/10/1989"}
        ]
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
      },
      setupFormateur(prenomFormateur : string) : void {
        this.formateurDuJour = prenomFormateur
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
  <h2>Computed properties</h2>
  <label for="lastname">Nom de famille</label>
  <input id="lastname" type="text" v-model="lastname">
  <label for="firstname">Prénom</label>
  <input id="firstname" type="text" v-model="firstname">
  <div>Bienvenue {{fullname}} ! </div>
 
  <!-- Class & Style Directives -->
  <h2>Directives de class et de style</h2>
  <button @click="isGreen = !isGreen">Vert</button>
  <button @click="isBold = !isBold">Gras</button>  
  <button @click="isGiant = !isGiant">Giant</button>  
  <div :class="{ green : isGreen, bold : isBold, giant : isGiant }">Ma balise qu'on va styliser</div>
  <div :style="{ fontSize : fontSize, fontWeight : 'bold'}">Texte avec style</div>

  <!-- Directives conditionnelles -->
  <h2>Directives conditionnelles</h2>
  <button @click="isVisible = !isVisible">Visible/Invisible</button>
  <div v-if="isVisible">Coucou</div>
  <div v-else>Hibou</div>

  <!-- Directive boucle -->
  <h2>Directive boucle</h2>
  <div v-for="(formateur, index) in formateurs" :key="index">
    <div>{{formateur}} - {{index}}</div>
  </div>

  <div>fonction aussi avec le of</div>
   <div v-for="formateur of formateurs">
    <div class="italic">{{formateur}}</div>
  </div>

  <!-- Component props emit -->
  <h2>Component avec props et emit</h2>
  <div>Le formateur du jour est {{formateurDuJour}}</div>
  <!-- <Card lastname="Beurive" firstname="Aude" birthdate="16/10/1989"></Card> -->
  <div class="flex">
    <div v-for="formateur of formateursBis">
    <!-- <Card lastname="formateur.lastname" firstname="formateur.firstname" birthdate="formateur.birthdate"></Card> -->
    <Card :lastname="formateur.lastname" :firstname="formateur.firstname" :birthdate="formateur.birthdate" @who="setupFormateur">
      <div>Formateur chez Bstorm</div>
    </Card>
    </div>
  </div>


  <br>
    <br>
      <br>
        <br>
          <br>
            <br>
             <br>
    <br>
      <br>
        <br>
          <br>
            <br>
             <br>
    <br>
      <br>
        <br>
          <br>
            <br>
             <br>
    <br>
      <br>
        <br>
          <br>
            <br>

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