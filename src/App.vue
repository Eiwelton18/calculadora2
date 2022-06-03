<template>
  <div id="app">
      
      <Calculator>
              
      </Calculator>
        
  </div>
</template>

<script>
import Calculator from './main/Calculator.vue';
export default {
    components: { Calculator }
}
</script>

<style>


*{
    font-family: 'Arial Narrow Regular', sans-serif;
    font-size: larger;
    
}

body{
    margin: 0;

}

/*
Button{
    
    border-radius: 1px;
}
*/


#app{
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
    align-items: center;
    text-align: center;
        
    color: rgb(255, 255, 255);
    background: rgb(59, 58, 58);
}
</style>