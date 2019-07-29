<template>
  <form @submit.prevent>
    <div class="field">
      <label for="billAmount">Bill Amount</label>
      <input
        id="billAmount"
        v-model.number="fields.billAmount"
        type="number"
        @input="$emit('submit', fields)"
      >
    </div>
    <div class="field">
      <label for="tipPercentage">Tip (%)</label>
      <increment-field
        v-model.number="fields.tipPercentage"
        :increment="5"
        :min="0"
        id="tipPercentage"
        @input="$emit('submit', fields)"
      />
    </div>
    <div class="field">
      <label for="split">Split</label>
      <increment-field
        v-model.number="fields.split"
        :increment="1"
        :min="1"
        id="split"
        @input="$emit('submit', fields)"
      />
    </div>
  </form>
</template>

<script>
import IncrementField from "./IncrementField";
export default {
  name: "TipForm",
  data() {
    return {
      fields: {
        billAmount: 0,
        tipPercentage: 0,
        split: 1
      }
    };
  },
  components: {
    IncrementField
  }
};
</script>

<style lang="scss" scoped>
form {
  padding: 0 2rem 2rem;
}

.field {
  padding-bottom: 1rem;
}

label {
  display: block;
  text-align: left;
  font-weight: 600;
}

input {
  width: 100%;
  padding: 8px 16px;
  font-size: 16px;
  line-height: 28px;
  border: 1px solid #eee;
  border-radius: 4px;
}
</style>
