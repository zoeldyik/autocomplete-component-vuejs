<template>
  <div id="app">
    <b-container>
      <b-row>
        <b-col md="6" class="offset-md-3">
          <app-hello v-if="items" :items="items"></app-hello>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    "app-hello": HelloWorld
  },
  data() {
    return {
      items: [
        "Apple",
        "Banana",
        "Orange",
        "Mango",
        "Pear",
        "Peach",
        "Grape",
        "Tangerine",
        "Pineapple",
        "Dragon Fruit"
      ]
    };
  }
};
</script>

<style>
#app {
  height: 100vh;
  background-color: #343a40;
}
</style>
