<template>
  <grid :allCoffees="allCoffees" @setFeatureEvent="setFeature" />

  <div id="featured" v-if="featuredCoffee.image">
    <div>
      <img :src="featuredCoffee.image" />

      <h3>{{ featuredCoffee.name }} {{ featuredCoffee.price }}€</h3>
    </div>
  </div>
</template>

<script>
import Grid from "./Grid.vue";

export default {
  name: "CoffeeView",
  data() {
    return {
      featuredCoffee: {
        name: "",
        image: "",
        price: "",
      },
    };
  },
  components: {
    Grid,
  },
  props: {
    allCoffees: {
      type: Array,
      required: true,
    },
  },
  methods: {
    handleClick(coffee) {
      this.featuredCoffee.name = coffee.name;
      this.featuredCoffee.price = coffee.price;
      this.featuredCoffee.image = coffee.image;
      console.log(this.allCoffees);
    },
  },
};
</script>

<style scoped>
#container-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
}
#grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-auto-rows: 180px;
  gap: 50px;
}
img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  cursor: pointer;
}
.hide {
  display: none;
}
#featured {
  display: grid;
  align-items: center;
  justify-items: center;
}
#featured img {
  width: 300px;
  height: 300px;
}
h3,
h5 {
  text-align: center;
}
</style>
