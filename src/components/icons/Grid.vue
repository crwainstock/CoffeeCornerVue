<template>
  <div>
    <h2>Pick a favorite:</h2>
    <div id="grid">
      <div v-for="coffee in allCoffees" :key="coffee.id">
        <img :src="coffee.image" @click="handleClick(coffee)" />
        <h5>{{ coffee.name }} ({{ coffee.price }}€)</h5>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Grid",
  props: ["allCoffees"],
  methods: {
    handleClick(coffee) {
      this.$emit("setFeatureEvent", coffee);
    },
  },
};
</script>

<style>
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
</style>
