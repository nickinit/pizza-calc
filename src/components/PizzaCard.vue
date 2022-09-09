<template>
  <div class="card">
<!--    header-->
    <div class="card-header">
      <h2>Pizza #{{ pizza.id }}</h2>
      <button @click="cardClosed" class="btn default close">&#10006;</button>
    </div>
      <hr>
<!--    body-->
    <div class="card-body">
      <div class="form-control">
        <label for="d">Diameter</label>
        <input :value="pizza.d"  type="text" name="d">
      </div>
      <div class="form-control">
        <label for="price">Price</label>
        <input :value="pizza.price" type="text" name="price">
      </div>
      <div class="form-control">
        <label for="count">Count</label>
        <input :value="pizza.count" type="text" name="count">
      </div>
    </div>
  </div>
</template>



<script>
export default {
  name: "PizzaCard",
  props: {
    pizza: Object,
    index: Number
  },
  data() {
    // return {id:12}

  },
  methods: {
    cardClosed() {
      this.$emit('cardClosed', this.index)
    }
  },
  computed: {
    inputVal: {
      get() {
        return this.value;
      },
      set(val) {
        this.$emit('input', val);
      }
    }
  },
}
</script>










<style scoped>
.container {
display: flex;
	min-width: 1200px;
	flex-direction: row;
}

.card-header {
  /*display: grid;*/
  position: relative;
  display: flex;
  flex-direction: row;
  justify-content: center;
}

.card-header p {
  /*display: flex;*/
  /*flex-direction: ;*/
  justify-content: flex-end;
}

.card-header *{
	margin: 0 0 10px 0;
  text-align: center;

}

.card {
  /*display: flex;*/
  flex-direction: column;
  border: 2px solid rgb(96, 139, 168);
  border-radius: 5px;
  max-width: 150px;
  min-width: 145px;
  margin: 5px;
  /*margin: 0 0 10px 0;*/
  padding: 15px;
  /*border-inline-width: 10px;*/
  background-color: white;
}


hr {
  border: solid #ddd;
  border-width: 1px 0 0;
  clear: both;
  margin: 2px 0 20px;
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



.card-header h2 {
  /*display: flex;*/
  justify-self: center;
}

.card-header .close {
  position: absolute;
  top: -10px;
  right: -10px;
}

.btn {
  border: 0px solid black;
  background-color: white;
  /*color: black;*/
  color: #2c3e50;

  /*padding: 14px 28px;*/
  font-size: 16px;
  border-radius: 5px;
  cursor: pointer;
}

/* Gray */
.default {
  border-color: #e7e7e7;
}

.default:hover {
  background: #e7e7e7;
}


</style>
