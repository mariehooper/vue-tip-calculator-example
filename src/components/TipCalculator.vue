<template>
  <div class="calculator">
    <h1>Tip Calculator</h1>
    <tip-form @submit="calculateBillTotal"/>
    <div class="total">
      <span>Split Bill Total:</span>
      <span class="split-total">${{ splitBillTotal.toFixed(2) }}</span>
    </div>
  </div>
</template>

<script>
import TipForm from "./TipForm";
export default {
  name: "TipCalculator",
  data() {
    return {
      splitBillTotal: 0
    };
  },
  components: {
    TipForm
  },
  methods: {
    calculateBillTotal({ billAmount, tipPercentage, split }) {
      this.splitBillTotal = (billAmount * (1 + tipPercentage / 100)) / split;
    }
  }
};
</script>

<style lang="scss" scoped>
.calculator {
  max-width: 400px;
  margin: 0 auto;
  box-shadow: 0 15px 35px 0 rgba(60, 66, 87, 0.1),
    0 5px 15px 0 rgba(0, 0, 0, 0.07);
  position: relative;
  background: white;
  border-radius: 4px;
}

h1 {
  margin: 0;
  padding: 2rem;
}

.total {
  background-color: #e8eaf682;
  padding: 1rem;
  border-radius: 4px;
  color: #3F51B5;
}

.split-total {
  display: block;
  font-size: 2rem;
  font-weight: 600;
}
</style>
