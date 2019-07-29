<template>
  <div id="app">
    <TipCalculator/>
  </div>
</template>

<script>
import TipCalculator from "./components/TipCalculator";

export default {
  name: "App",
  components: {
    TipCalculator
  }
};
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  position: relative;

  &::before {
    content: "";
    position: absolute;
    height: 824px;
    transform: skewY(-12deg);
    top: -300px;
    left: 0;
    right: 0;
    z-index: 0;
    background-color: #f7fafc;
    overflow: hidden;
  }
}

input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>
