<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent ({
  name: "Test",
  created() {},
  data() {
    return {
      secondes : 0,
      timer : 0,

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
    time() : string {
      let min = Math.floor(this.secondes/60);
      let sec = this.secondes % 60;
      let heu = Math.floor(min/60);
      min = min%60;
      return `${(heu > 9 ? heu : '0'+heu)} : ${min > 9 ? min : '0'+min} : ${sec > 9 ? sec : '0'+sec}`;
    }
  },
  props: {},
  methods: {
    start() : void {
      this.timer = setInterval(() => { this.secondes ++ }, 1000);
    },
    pause() : void {
      clearInterval(this.timer);
      this.timer = 0;
    },
    reset() : void {
      this.secondes = 0;
      this.pause();
    },
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
  <div>
    <h2>Exercice Timer</h2>
    <div>{{time}}</div>
    <button @click="start()" :disabled="timer!=0">Start</button>
    <button @click="pause()" :disabled="timer==0">Pause</button>
    <button @click="reset()" :disabled="secondes==0">Reset</button>
  </div>

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