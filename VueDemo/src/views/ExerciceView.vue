<script lang="ts">
import { defineComponent } from "vue";
import Timer from "../components/Timer.vue";
export default defineComponent ({
  name: "Test",
  components : {
    Timer
  },
  created() {},
  data() {
    return {
      name : "",
      price : 0,
      quantity : 0,

      products : [
        { id : 0, name : "Pomme de terre", price : 1.50, quantity : 15},
        { id : 1, name : "Pommes", price : 0.37, quantity : 0}
      ]
    };
  },
  computed : {
  },
  props: {},
  methods: {
    addProduct(){
      this.products.push({ id : this.products.length, name : this.name, price : this.price, quantity : this.quantity});
      this.name = "";
      this.price = 0;
      this.quantity = 0;
    }
  },
});
</script>

<template>
  <h1>Exercices :</h1>
  <Timer/>

  <div>
    <h2>Exercice Liste Produits</h2>
    <table>
    <tr><th>Nom</th><th>Prix</th><th>Quantité</th></tr>
    <tr v-for="product in products" :key="product.id">
      <td>{{product.name}}</td>
      <td>{{product.price}}</td>
      <td v-if="product.quantity>0">{{product.quantity}}</td>
      <td v-else :class="{ 'alert-stock' : product.quantity == 0}">Plus de stock</td>
    </tr>
    </table>

    <input type="text" v-model="name">
    <input type="number" v-model="price">
    <input type="number" v-model="quantity">
    <button @click="addProduct()">Ajouter produit</button>
  </div>
</template>

<style scoped>
  .alert-stock {
    color : darkred;
  }
</style>