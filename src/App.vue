<template>
  <main>
    <nav>
      <button @click="coffeeView = false" class="selectedView">
        Add Coffee
      </button>
      <button @click="coffeeView = true" class="selectedView">
        Choose Your Cup
      </button>
    </nav>
    <div class="formContainer">
      <h1>Coffee Corner</h1>
      <coffee-form v-if="!coffeeView" @add="addCoffee" />
      <coffee-view v-else :allCoffees="allCoffees" />
    </div>
  </main>
</template>

<script>
import CoffeeForm from "./components/icons/CoffeeForm.vue";
import CoffeeView from "./components/icons/CoffeeView.vue";
import MyCoffees from "./components/icons/MyCoffees";

export default {
  name: "app",
  components: {
    coffeeForm: CoffeeForm,
    coffeeView: CoffeeView,
  },
  data() {
    return {
      coffeeView: false,
      allCoffees: [],
    };
  },
  methods: {
    addCoffee(coffee) {
      this.allCoffees.push(coffee);
      this.coffeeView = true;
    },
  },
  created() {
    this.allCoffees = MyCoffees;
  },
};
</script>

<style>
/* This worked for importing and using Google fonts */
@import url("https://fonts.googleapis.com/css2?family=Noto+Sans:wght@300;400;700&display=swap");
html,
body {
  font-family: "Noto Sans", sans-serif;
}
nav {
  text-align: right;
}
</style>
