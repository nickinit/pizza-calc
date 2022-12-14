<template>
  <div class="card-list">


      <pizza-card v-for="(pizza, i) in pizzas"
                  :key="pizza.id"
                  v-model="pizzas[i]"
                  @closeCard="closeCard"
                  @keyup="calculateOverpayment"
      ></pizza-card>


  </div>
  <div class="new-card-container">
    <button class="new-card-button default" @click="addCard">Need more pizza</button>
  </div>



</template>

<script>
import PizzaCard from "@/components/PizzaCard";

export default {
  name: "PizzaList",
  components: {
    PizzaCard
  },
  methods: {
    log(){console.log(this.pizzas)},
    addCard() {
      const nextId = this.findMaxId(this.pizzas) + 1
      this.pizzas.push({
        id: this.pizzas.length > 0 ? nextId : 1,
        d: undefined,
        price: undefined,
        count: 1,
        overpayment: undefined
      })
    },

    closeCard(id) {
      this.pizzas = this.pizzas.filter(a => a.id !== id)
      this.pizzas.length === 1 ? this.pizzas[0].overpayment = undefined : this.calculateOverpayment()
    },

    findMaxId(arr) {
      const ids = arr.map(object => {
        return object.id;
      });
      return Math.max(...ids);
    },

    // findMinOverpayment(arr) {
    //   arr.sort((a, b) => a.price / a.count / a.d - b.price / b.count / b.d);
    // },

    findMinPricePerCm(arr) {
      const prices = arr.map(object => {
        object.ppc = (isNaN(object.ppc) ? Infinity : object.ppc)
        return object.ppc;
      });
      return Math.min(...prices);
    },

    fillPricePerCm() {
      this.pizzas.forEach(function(e){
        e.ppc = e.price / e.count / ((e.d / 2 ) ** 2 * Math.PI) // TODO add dimension selection (square, diameter, etc)
      })
      // console.log(this.pizzas)
    },

    calculateOverpayment() {
      this.fillPricePerCm()
      const minPricePerCm = this.findMinPricePerCm(this.pizzas)
      this.pizzas.forEach(function(e){
        e.overpayment = (e.ppc - minPricePerCm) / minPricePerCm * 100
      })

    }
  },

  data() {
    return {
      pizzas: [{
        id: 1,
        d: undefined,
        price: undefined,
        count: 1,
        overpayment: undefined
      }, {
        id: 2,
        d: undefined,
        price: undefined,
        count: 1,
        overpayment: undefined
      }]

    }
  },

}
</script>

<style scoped>
.card-list {
  display: flex;
  flex-direction: row;
  justify-content: center;
  flex-wrap: wrap;
  /*margin: 5px;*/
  margin-top: 0;
}

.new-card-container {
  display: flex;
  justify-content: center;
}

.new-card-button {
/*
  position: fixed;
  top: 75px;
  right: 2px;
  border-radius: 100px;
  height: 100px;
  width: 100px;
*/
  width: 80%;

  /*border-radius: 15px;*/
  font-family: 'Rubik Burned', cursive;
  font-size: 28pt;
  margin: 5px 5px 5px 0;
  cursor: pointer;
  border: 2px solid rgb(96, 139, 168); /*rgb(96, 139, 168);*/

  font-weight: bold;
  background: #efefef;

  color: #2c3e50;

  /*padding: 14px 28px;*/
  /*font-size: 16px;*/
  border-radius: 5px;
}
/* Gray */
.default {

}

.default:hover {
  /*background: #efefef;*/
  /*background-color: white;*/
  color: #2c3e50;

  /*border: 2px solid red;*/
}


/*
.new-card-no-cards {
  border: 2px solid rgb(96, 139, 168);
  border-radius: 5px;
  max-width: 150px;
  min-width: 145px;
  min-height: 173px;
  max-height: 173px;
  margin: 5px;
  !*margin: 0 0 10px 0;*!
  padding: 15px;
  cursor: pointer;
  !*border-inline-width: 10px;*!
  background-color: white;
}
*/



</style>
