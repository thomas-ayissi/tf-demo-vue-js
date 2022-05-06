<template>
  <div class="chapter">
    <h2>Exercice Liste Produits</h2>
    <div class="demoflex">
    <table>
      <tr>
        <th>Nom</th>
        <th>Prix</th>
        <th>Quantité</th>
      </tr>
      <tr v-for="product in products" :key="product.id">
        <td>{{ product.name }}</td>
        <td>{{ product.price }}</td>
        <td v-if="product.quantity > 0">{{ product.quantity }}</td>
        <td v-else :class="{ 'alert-stock': product.quantity == 0 }">Plus de stock</td>
      </tr>
    </table>

    <div>
      <h3>Ajouter un nouveau produit :</h3>
      <div class="group">
      <label for="name">Nom du produit :</label>
      <input id="name" type="text" v-model="name">
      </div>
      <div class="group">
            <label for="price">Prix du produit :</label>
      <input id="price" type="number" v-model="price">
      </div>
      <div class="group">
            <label for="quantity">Quantité du produit :</label>

      <input id="quantity" type="number" v-model="quantity">
      </div>
      <button class="btn" @click="addProduct()">Ajouter produit</button>
    </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "Test",
  created() { },
  data() {
    return {
      name: "",
      price: 0,
      quantity: 0,

      products: [
        { id: 0, name: "Pomme de terre", price: 1.50, quantity: 15 },
        { id: 1, name: "Pommes", price: 0.37, quantity: 0 }
      ]
    };
  },
  methods: {
    addProduct() {
      this.products.push({ id: this.products.length, name: this.name, price: this.price, quantity: this.quantity });
      this.name = "";
      this.price = 0;
      this.quantity = 0;
    }
  },
});
</script>

<style scoped>
 .alert-stock {
    color : darkred;
  }
</style>