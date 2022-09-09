<template>
<!--  <HelloWorld msg="Welcome to Your Vue.js App"/>-->
<!--  <PizzaCard />-->
  <div class="content">
    <PizzaList />
  </div>

</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import PizzaCard from "@/components/PizzaCard";
import PizzaList from "@/components/PizzaList";

export default {
  name: 'App',
  components: {
    // HelloWorld,
    // PizzaCard,
    PizzaList
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

.content {
  max-width: 720px;
  background-color: #f6f6f6;
  margin: auto;

}
</style>
