<template>
  <grid :allCoffees="allCoffees" @setFeatureEvent="setFeature" />
  <Cart :chosenItems="chosenItems" :class="{ hide: !chosenItems.length }" />
  <!-- <div id="featured" v-if="featuredCoffee.image">
    <div>
      <img :src="featuredCoffee.image" />

      <h3>{{ featuredCoffee.name }} {{ featuredCoffee.price }}€</h3>
    </div> -->
  <!-- </div> -->
</template>

<script>
import Grid from "./Grid.vue";
import Cart from "./Cart.vue";

export default {
  name: "CoffeeView",
  data() {
    return {
      searchTerm: "",
      chosenItems: [],
    };
  },
  components: {
    Grid,
    Cart,
  },
  props: {
    allCoffees: {
      type: Array,
      required: true,
    },
  },
  methods: {
    // handleClick(coffee) {
    //   this.featuredCoffee.name = coffee.name;
    //   this.featuredCoffee.price = coffee.price;
    //   this.featuredCoffee.image = coffee.image;
    //   console.log(this.allCoffees);
    // },
    setFeature(coffee) {
      this.chosenItems.push(coffee);
    },
  },
};
</script>

<style scoped>
#container-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  margin-top: 50px;
}
.hide {
  display: none;
}
/* #featured {
  display: grid;
  align-items: center;
  justify-items: center;
}
#featured img {
  width: 300px;
  height: 300px;
} */
h3,
h5 {
  text-align: center;
}
</style>
