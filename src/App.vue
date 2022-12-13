<template>
<!--  <HelloWorld msg="Welcome to Your Vue.js App"/>-->
<!--  <PizzaCard />-->
  <header-section />
  <div class="content">
    <PizzaList />
  </div>

  <footer-section />
</template>

<script>

import PizzaList from "@/components/PizzaList";
import HeaderSection from "@/components/HeaderSection.vue";
import FooterSection from "@/components/FooterSection.vue";

export default {
  name: 'App',
  components: {
    FooterSection,
    HeaderSection,
    PizzaList
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Rubik+Burned&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Slackey&display=swap');


#app {
  /*font-family: Avenir, Helvetica, Arial, sans-serif;*/
  /*font-family: 'Press Start 2P', cursive;*/
  /*font-family: 'Rubik Burned', cursive;*/
  font-family: 'Slackey', cursive;

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  /*margin-top: 60px;*/
}

.content {
  max-width: 1024px;
  margin: auto;
}
</style>
