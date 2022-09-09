<template>
  <h2 >{{ foo }}</h2>
  <div class="flex">
    <pizza-card @cardClosed="cardClosed"
                v-for="(pizza, index) in proposals"
                :key="index"
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
    valueChanged: function (d){alert(d)},
    addNewElement: function (){
      let p = this.proposals
      if (p.length > 0) {
        p.push({id: p[p.length - 1].id + 1})
      } else {
        p.push({id: 1})
      }


    },
    cardClosed: function (id){this.proposals.splice(id, 1)}
  },
  data() {
    return {
      searchText: '',
      foo: {},
      proposals: [
        {
          id: 1
          // d: 25,
          // price: 150,
          // count: 1
        },
        {
          id: 2
          // d: 30,
          // price: 1200,
          // count: 1
        },
      ]
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
