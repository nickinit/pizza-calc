<template>
  <div class='container'>
  <div class="card">
  <div class="card-header">
    <h2>Pizza #{{ pizza.id }}</h2>
    <hr>
  </div>
    <div class="content">
      <div class="form-control">
        <label for="d">Diameter</label>
        <input v-model="pizza.d" type="text" name="d">
      </div>
      <div class="form-control">
        <label for="price">Price</label>
        <input v-model="pizza.price" type="text" name="price">
      </div>
      <div class="form-control">
        <label for="count">Count</label>
        <input v-model="pizza.count" type="text" name="count">
      </div>
    </div>
<!--    <footer>Card footer</footer>-->
  </div>

  </div>
</template>

<script>
export default {
  name: "PizzaCard",
  props: {
    id: Number,
    d: Number,
    price: Number,
    count: {
      type: Number,
      default: 1,
    }
  },
  data() {
    return {
      pizza: {
        id: 1,
        d: 25,
        price: 150,
        count: 1
      }
    };
  },
}
</script>

<style scoped>
.container {
display: flex;
	min-width: 1200px;
	flex-direction: row;
}

.card-header *{
	margin: 0 0 10px 0;
  text-align: center;
}

.card {
  display: flex;
  flex-direction: column;
  border: 2px solid rgb(96, 139, 168);
  border-radius: 5px;
  max-width: 300px;
  min-width: 145px;
  /*margin: 0 10px;*/
  padding: 15px;
  /*border-inline-width: 10px;*/

}

hr {
  border: solid #ddd;
  border-width: 1px 0 0;
  clear: both;
  margin: 22px 0 21px;
  height: 0;


}

.form-control {
  margin: 2px 0 2px 0;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.form-control input {
  width: 50px;
}

input[type="text"] {
  font-family: inherit; /* 1 */
  font-size: inherit; /* 1 */
  line-height: inherit; /* 1 */
  margin: 0; /* 2 */
}
input {
  color: #2c3e50;
  text-align: right;
}

input:focus {
  color: #2c3e50;
}


</style>
