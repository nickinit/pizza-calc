<template>
<!--  <HelloWorld msg="Welcome to Your Vue.js App"/>-->
<!--  <PizzaCard />-->
  <div class="content">
    <PizzaList />
  </div>

</template>

<script>

import PizzaList from "@/components/PizzaList";

export default {
  name: 'App',
  components: {
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
  max-width: 1024px;
  margin: auto;

}
</style>
