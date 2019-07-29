<template>
  <div class="field-wrap">
    <button type="button" class="increment plus" @click="incrementDown">-</button>
    <input
      :id="id"
      :value="value"
      type="number"
      :min="min"
      :max="max"
      :step="increment"
      @input="$emit('input', $event.target.value)"
    >
    <button type="button" class="increment minus" @click="incrementUp">+</button>
  </div>
</template>

<script>
export default {
  name: "IncrementField",
  props: {
    id: {
      type: String,
      required: true
    },
    increment: {
      type: Number,
      required: true
    },
    min: {
      type: Number,
      required: false,
      default: 0
    },
    max: {
      type: Number,
      required: false
    },
    value: {
      type: Number,
      required: true
    }
  },
  methods: {
    incrementUp() {
      this.$emit("input", this.value + this.increment);
    },
    incrementDown() {
      if (this.value - this.increment >= this.min) {
        this.$emit("input", this.value - this.increment);
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.field-wrap {
  display: flex;
  .increment {
    background: none;
    width: 3rem;
    font-size: 1.5rem;
    border: 1px solid #eee;
    background-color: #f3f4fb;
    color: #3f51b5;
    line-height: 1.2rem;
    &.plus {
      border-radius: 4px 0 0 4px;
      margin-left: -1px;
    }
    &.minus {
      border-radius: 0 4px 4px 0;
      margin-right: -1px;
    }
  }

  input {
    width: 100%;
    padding: 8px 16px;
    font-size: 16px;
    line-height: 28px;
    border: 1px solid #eee;
    border-radius: 0;
  }
}
</style>
