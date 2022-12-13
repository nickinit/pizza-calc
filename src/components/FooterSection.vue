<template>
  <div class="footer">
    <span>&copy; PizzaCalc Project</span>
    <a href="https://t.me/pizzacalc" class="fa fa-telegram" style="font-size: 32pt; color: #2c9fd8;"></a>
    <a href="https://github.com/suppchik/pizza-calc" class="fa fa-github" style="font-size: 38pt; color: #000"></a>
  </div>
</template>

<script>
export default {
  name: "FooterSection"
}
</script>

<style scoped>
  .footer {
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 24pt;
  }

  .footer span {
    margin: 0 10px 0 10px;
  }

  .footer a {
    text-decoration: none;
    margin: 1px;
  }
</style>