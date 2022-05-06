<template>
  <div class="chapter">
      <h2>Component avec props et emit</h2>
    <div class="demoflexcol">
      <div class="self-center text-xl mb-3">Le formateur du jour est {{ formateurDuJour }}</div>
      <!-- <Card lastname="Beurive" firstname="Aude" birthdate="16/10/1989"></Card> -->
      <div class="flex">
        <div v-for="formateur of formateursBis">
          <!-- <Card lastname="formateur.lastname" firstname="formateur.firstname" birthdate="formateur.birthdate"></Card> -->
          <Card :lastname="formateur.lastname" :firstname="formateur.firstname" :birthdate="formateur.birthdate" :avatar="formateur.avatar"
            @who="setupFormateur">
            <div>Formateur à votre écoute !</div>
          </Card>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Card from "./Card.vue"
export default defineComponent({
  name: "DemoComponent",
  created() { },
  components: {
    Card
  },
  data() {
    return {
      formateurDuJour: "...",
      formateursBis: [
        { id: 0, lastname: "Ly", firstname: "Khun", birthdate: "06/05/1982", avatar : "khun.png" },
        { id: 1, lastname: "Strimelle", firstname: "Aurélien", birthdate: "01/11/1989", avatar : "aurelien.png" },
        { id: 2, lastname: "Beurive", firstname: "Aude", birthdate: "16/10/1989", avatar : "aude.png" },
        { id: 3, lastname: "Person", firstname : "Mike", birthdate: "17/03/1982", avatar : "mike.png"}
      ]
    };
  },
  methods: {
    setupFormateur(prenomFormateur: string): void {
      this.formateurDuJour = prenomFormateur
    }
  },
});
</script>

<style lang="scss" scoped>
</style>