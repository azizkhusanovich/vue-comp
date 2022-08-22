<template>
  <div class="container">
    <div class="card">
      <p>Lorem ipsum dolor sit amet.</p>

      <h2>Dynamic components</h2>
      <button class="btn" :class="firstClass" @click="activeClass = 'one'">
        One
      </button>
      <button class="btn" :class="secondClass" @click="activeClass = 'two'">
        Two
      </button>
    </div>

    <keep-alive>
      <component :is="move"></component>
    </keep-alive>

    <!-- <app-card-one></app-card-one> -->
    <!-- <app-card-two></app-card-two> -->
  </div>
</template>

<script>
import AppCardOne from "./components/AppCardOne.vue";
import AppCardTwo from "./components/AppCardTwo.vue";
export default {
  data() {
    return {
      activeClass: "one", // two
    };
  },
  components: {
    AppCardOne,
    AppCardTwo,
  },
  computed: {
    move() {
      return "app-card-" + this.activeClass;
    },
    firstClass() {
      return this.activeClass === "one" ? "primary" : "";
    },
    secondClass() {
      return this.activeClass === "two" ? "primary" : "";
    },
  },
};
</script>

<style>
</style>