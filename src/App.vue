<template>
  <div id="app">
    <Calculator> </Calculator>
  </div>
</template>

<script>
import Calculator from "./main/Calculator.vue";

export default {
  components: { Calculator },
};
</script>

<style>
* {
  font-family: "Arial Narrow Regular", sans-serif;
  font-size: larger;
}

body {
  background-color: rgb(64, 60, 60);
}

/*
Button{
    
    border-radius: 1px;
}
*/

#app {
  display: flex;
  flex-direction: column;
  height: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding-top: 100px;
  color: rgb(255, 255, 255);
  background: rgb(59, 58, 58);
}
</style>