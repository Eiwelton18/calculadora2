<template>
  <Button class="Button" @click="$emit('onClickButton', label)" :class="{ double, triple, operation }">
  {{ label}}
  </Button>
</template>

<script>
export default {

    props:{
      label:{},
      operation: {type: Boolean},
      double: {type: Boolean},
      triple: {type: Boolean}

    }

}
</script>

<style>
/*
.Button{
  
  align-items: center;
  justify-content: center;
    
}

.Button.double{
  grid-column: span 2;
}

.Button.triple{
  grid-column: span 3;

}

.Button.operation{
  background-color: rgba(195, 192, 247, 0.137);
  color: rgb(255, 255, 255);
}
*/

</style>