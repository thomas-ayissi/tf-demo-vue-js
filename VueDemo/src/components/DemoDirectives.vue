<template>
  <div class="chapter">
    <h2>Les directives</h2>
    <div class="demoflex">
      <div class="democard">
        <h3 class="democardtitle">Directives de class et de style</h3>
        <button class="btn" @click="isGreen = !isGreen">Vert</button>
        <button class="btn" @click="isBold = !isBold">Gras</button>
        <button class="btn" @click="isGiant = !isGiant">Giant</button>
        <div :class="{ green: isGreen, bold: isBold, giant: isGiant }">Ma balise qu'on va styliser</div>
        <div :style="{ fontSize: fontSize, fontWeight: 'bold' }">Texte avec style</div>
      </div>

      <div class="democard">
        <h3 class="democardtitle">Directives conditionnelles</h3>
        <button class="btn" @click="isVisible = !isVisible">Visible/Invisible</button>
        <div v-if="isVisible">Coucou</div>
        <div v-else>Hibou</div>
      </div>

      <div class="democard">
        <h3 class="democardtitle">Directive boucle</h3>
        <div class="mb-3">
          <h4>Liste des formateurs avec "in" et index</h4>
          <div v-for="(formateur, index) in formateurs" :key="index">
            <div>{{ formateur }} - {{ index }}</div>
          </div>
        </div>

        <h4>Liste des formateurs avec "of"</h4>
        <div v-for="formateur of formateurs">
          <div>{{ formateur }}</div>
        </div>
      </div>
    </div>

  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "DemoDirectives",
  created() { },
  data() {
    return {
      isGreen: false,
      isBold: false,
      isGiant: false,
      fontSize: '24px',
      weight: 'bold',
      isVisible: true,
      formateurs: ['Khun', 'Steve', 'Aurélien', 'Loïc', 'Aude'],
    };
  },
  methods: {},
});
</script>

<style lang="scss" scoped>
</style>