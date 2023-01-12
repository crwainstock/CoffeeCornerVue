<template>
  <div>
    <h2>Pick a favorite:</h2>
    <div id="container-grid">
      <div id="grid">
        <div v-for="coffee in allCoffees" :key="coffee.id">
          <img :src="coffee.image" @click="handleClick(coffee)" />
          <h5>{{ coffee.name }} ({{ coffee.price }}€)</h5>
        </div>
      </div>
    </div>

    <div id="featured" :class="{ hide: !featuredCoffee.image }">
      <div>
        <img :src="featuredCoffee.image" />

        <h3>{{ featuredCoffee.name }} {{ featuredCoffee.price }}</h3>
      </div>
    </div>
  </div>
</template>

<script>
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
  margin-top: 50px;
  /* Need to finish this styling. Featured section is below, not to the side.*/
}
#featured img {
  width: 300px;
  height: 300px;
}
h5 {
  text-align: center;
}
</style>
