<template>
  <div>
    <h2>Add a coffee</h2>
    <form @submit.prevent="addCoffee">
      <input type="text" v-model="name" placeholder="Name" />
      <input type="text" v-model="price" placeholder="Price" />
      <input type="url" v-model="image" placeholder="Image URL" />

      <button type="submit">Add Coffee</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "CoffeeForm", //Don't forget the quotes here!
  data() {
    return {
      name: "",
      price: "",
      image: "",
      id: 0,
    };
  },
  methods: {
    addCoffee() {
      this.id++;
      let newCoffee = {
        name: this.name,
        price: this.price,
        image: this.image,
        id: this.id,
      };
      this.$emit("add", newCoffee);
      this.coffeeName = this.coffeeImg = ""; //Setting input forms back to empty
      this.coffeePrice = 0; //Setting input field to 0
      console.log(newCoffee);
    },
  },
};
</script>

<style></style>
