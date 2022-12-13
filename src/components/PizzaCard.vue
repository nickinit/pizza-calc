<template>
  <div class="card"  :class="{ bestProposal : isTheBest(value.overpayment) }"   >
<!--    header-->
    <div class="card-header">
      <h2>Pizza #{{ modelValue.id }}</h2>
      <button @click="closeCard(value.id)" class="btn default close">&#10006;</button>
    </div>
      <hr>
<!--    body-->
    <div class="card-body">
      <div class="form-control">
        <label for="d">Size...</label>
        <input
           type="text" v-model.number="value.d" placeholder="cm&#178;">
      </div>
      <div class="form-control">
        <label for="price">Price...</label>
        <input type="text"  v-model.number="value.price" placeholder="&#8381;">
      </div>
      <div class="form-control">
        <label for="count">Count...</label>
        <input type="text"  v-model.number="value.count">
      </div>
      <div class="form-control">
        <span class="danger-text"  v-if="isFinite(value.overpayment) && value.overpayment > 0">
          Overpayment: {{ Math.round(value.overpayment) }}%
        </span>
        <span v-else-if="value.overpayment === 0">
          This is the best deal!
        </span>

      </div>
    </div>
  </div>
</template>



<script>
export default {
  name: "PizzaCard",
  props: ['modelValue'],
  emits: ['update:modelValue', 'closeCard'],
  computed: {
    value: {
      get() {
        return this.modelValue
      },
      set(value) {
        this.$emit('update:modelValue', value)
      }
    }
  },
  // data() {},
  methods: {
    closeCard(id){
      this.$emit('closeCard', id)
    },
    isTheBest(overpayment){
      return overpayment === 0
    }
  },

}
</script>










<style scoped>


.card-header {
  /*display: grid;*/
  position: relative;
  display: flex;
  flex-direction: row;
  justify-content: center;
  font-size: 10pt;
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
  /*width: 150px;*/
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

.bestProposal {
  outline: none;
  border-color: forestgreen;
  box-shadow: 0 0 10px yellowgreen;
  text-align: center;
  /*background: #42b983;*/
}

.bestProposal span {
  color: forestgreen;
  margin-top: 10px;
  font-size: 10pt;
  text-align: center;
}

.danger-text {
  color: red;
  margin-top: 10px;
  font-size: 10pt;
}

</style>
