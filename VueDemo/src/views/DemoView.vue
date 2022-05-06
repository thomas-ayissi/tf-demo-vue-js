<script lang="ts">
import Card  from "../components/Card.vue";
import DemoBinding from "../components/DemoBinding.vue";
import DemoDirectives from "../components/DemoDirectives.vue";
import { defineComponent } from "vue"
  export default defineComponent ({
    components : {
      Card,
      DemoBinding,
      DemoDirectives
    },
    data() {
      return {
        maClass : "green",


        formateurDuJour : "",
        formateursBis : [
          { id : 0, lastname : "Ly" , firstname : "Khun" , birthdate : "06/05/1982"},
          { id : 1, lastname : "Strimelle", firstname : "Aurélien", birthdate : "01/11/1989"},
          { id : 2, lastname : "Beurive", firstname : "Aude", birthdate : "16/10/1989"}
        ]
      }
    },
    computed : {

    },
    methods : {
      setupFormateur(prenomFormateur : string) : void {
        this.formateurDuJour = prenomFormateur
      }

    }
  })
</script>

<template>
  <h1>Demo VueJS</h1>
  <DemoBinding></DemoBinding>
  <DemoDirectives></DemoDirectives>
  
 
  

  

  

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