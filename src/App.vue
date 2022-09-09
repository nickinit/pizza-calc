<template>
<!--  <HelloWorld msg="Welcome to Your Vue.js App"/>-->
  <PizzaCard />
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import PizzaCard from "@/components/PizzaCard";

export default {
  name: 'App',
  components: {
    // HelloWorld,
    PizzaCard
  }
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  margin-top: 60px;
}
</style>
