<template>
  <div>{{ proposals }}</div>
  <div>{{ the_best }}</div>
  <div class="flex">
    <pizza-card @cardClosed="cardClosed"
                v-for="(pizza, index) in proposals"
                :key="index"
                @dataChanged="dataChanged"
                :the_best="the_best"
                :pizza="pizza" :index="index"/>

    <button @click="addNewElement " class="new-card-button">+</button>
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
    addNewElement: function (){

      if (this.proposals.length > 0) {
        console.log('max', [...this.proposals].sort((a,b) => b.id - a.id)[0])
        this.proposals.push({
          id: [...this.proposals].sort((a,b) => b.id - a.id)[0].id + 1,
          count: 1,
          price:undefined,
          d: undefined})
        // p.push({id: p[p.length - 1].id + 1})
      } else {
        this.proposals.push({id: 1, count: 1, price:undefined, d: undefined})
      }
    },
    cardClosed: function (id){
      this.proposals = this.proposals.filter(x => x.id !== id)
      // this.proposals.splice(id, 1)
      console.log('proposals after filter: ',this.proposals)
      this.dataChanged()
      console.log('data changed after cloalskdjf:', this.the_best)
      return this.proposals
    },
    dataChanged: function () {
      // let changedPizza = this.proposals.find(x => x.id === e.id);
      // changedPizza = e
      // console.log('DO',this.proposals)
      let propNew = [...this.proposals]
      propNew.sort(function (a, b) {


        if ((a.price / a.count / a.d) > (b.price / b.count / b.d)) {
          return 1;
        }
        if ((a.price / a.count / a.d) < (b.price / b.count / b.d)) {
          return -1;
        }
        // a должно быть равным b
        return 0;
      });
      // console.log('posle', this.proposals)
      this.the_best = propNew[0]
      return true
    }

  },
  data() {
    return {
      proposals: [
        {
          id: 1,
          d: undefined,
          price: undefined,
          count: undefined
        },
        {
          id: 2,
          d: undefined,
          price: undefined,
          count: undefined
        },
      ],
      the_best: undefined
    }
  },

}
</script>

<style scoped>
.flex {
  display: flex;
  flex-direction: row;
  justify-content: center;
  flex-wrap: wrap;
  margin: 5px;
}

.new-card-button {
  margin: 5px 5px 5px 0px;
}



</style>
