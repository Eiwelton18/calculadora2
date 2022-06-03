<template>
<h1 center> CALCULADORA</h1>
  <div class="calculator">
      
      <Display :value="displayValue"  />
      <Button label="AC" triple @onClickButton="limpaTela" class="p-button-raised p-button-secondary" />
      <Button label="/" operation @onClickButton="setOperation" class="p-button-raised p-button-secondary"/>
      <Button label="7"  @onClickButton="addDigit" class="p-button-raised p-button-secondary"/>
      <Button label="8" @onClickButton="addDigit" class="p-button-raised p-button-secondary"/>
      <Button label="9" @onClickButton="addDigit" class="p-button-raised p-button-secondary"/>
      <Button label="*" operation @onClickButton="setOperation" class="p-button-raised p-button-secondary"/>
      <Button label="4" @onClickButton="addDigit" class="p-button-raised p-button-secondary"/>
      <Button label="5" @onClickButton="addDigit" class="p-button-raised p-button-secondary"/>
      <Button label="6" @onClickButton="addDigit" class="p-button-raised p-button-secondary"/>
      <Button label="-" operation @onClickButton="setOperation" class="p-button-raised p-button-secondary"/>
      <Button label="1" @onClickButton="addDigit" class="p-button-raised p-button-secondary" />
      <Button label="2" @onClickButton="addDigit" class="p-button-raised p-button-secondary"/>
      <Button label="3" @onClickButton="addDigit" class="p-button-raised p-button-secondary"/>
      <Button label="+" operation @onClickButton="setOperation" class="p-button-raised p-button-secondary"/>
      <Button label="0" double @onClickButton="addDigit" class="p-button-raised p-button-secondary"/>
      <Button label="."  @onClickButton="addDigit" class="p-button-raised p-button-secondary"/>
      <Button label="=" operation @onClickButton="setOperation" class="p-button-raised p-button-secondary"/>
   
      
  </div>
</template>

<script>
import Display from "../components/Display.vue"
import Button from "../components/Button.vue"

export default {
    data: () => {
        return{
            displayValue: "0",
            clearDisplay: false,
            operation: null,
            values: [0, 0],
            current: 0
        }
    },

    components:{ Display, Button },
    methods: {

        
        limpaTela(){
            Object.assign(this.$data, this.$options.data())
        },

        setOperation(operation){
            
            if (this.current === 0){
                this.operation = operation;
                this.current = 1;
                this.clearDisplay = true;
            } else {
                const equals = operation === "=";
                const currentOperation = this.operation;

                                
                    try {
                        this.values[0] = eval(
                            `${this.values[0]} ${currentOperation} ${this.values[1]}`
                        );
                       
                    } catch(e){
                        this.$emit('onError', e)
                    }

                    this.values[1] = 0

                    this.displayValue = this.values[0]
                    this.operation = equals ? null : operation
                    this.current = equals ? 0 : 1
                    this.clearDisplay = !equals


                    }
            
        },

        addDigit(n){
            if (n === "." && this.displayValue.includes(".") ) {
                return 
            }
            
            const clearDisplay = this.displayValue ==="0"  || this.clearDisplay

            const currentValue = clearDisplay ? "" : this. displayValue 
            const displayValue = currentValue + n

            this.displayValue = displayValue
            this.clearDisplay = false

            if ( n !== "."){
                const i = this.current
                const newValue = parseFloat(displayValue)
                this.values[i] = newValue
            }

        }
    }
}
</script>

<style>

.calculator{
    height: 330px;
    width: 240px;
    border-radius: 10px;
    overflow: hidden;
    background: #477eac36;
    display: grid;
    
    grid-template-columns: repeat(4, 25%);
    grid-template-rows: 1fr 52px 52px 52px 52px 52px;
  
}

</style>