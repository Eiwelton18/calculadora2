<template>
  <div class="Display">
      {{value}}
  </div>
</template>

<script>
export default {
  props: ['value'],

}
</script>

<style>
  .Display {
    grid-column: span 4;
    background: rgb(97, 95, 95);
   

    
    display: flex;
    justify-content: flex-end;
    align-items: flex-end;
    padding: 6px;
    font-size: 1.1em;
    overflow: hidden;
    text-overflow: hidden;
  }

</style>