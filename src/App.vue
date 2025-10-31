<script setup>
import { reactive } from 'vue';

const estado = reactive({
  n1: 0,
  n2: 0,
  signal: 'sum',
  })

  function calculate(){
    if (estado.signal === 'sum') {
      return estado.n1 + estado.n2
    } else if (estado.signal === 'sub') {
      return estado.n1 - estado.n2
    } else if (estado.signal === 'mult') {
      return estado.n1 * estado.n2
    } else if (estado.signal === 'division') {
      if (estado.n2 === 0){
        return "ERRO"
      } else {
        return estado.n1 / estado.n2
      }
    }
  };
</script>

<template>
<div class="container">
  <div class="calculator">
    <h2 class="h-one">Input the first number</h2>
    <input class="input inp-one" type="number" @keyup="evento => estado.n1 = Number(evento.target.value)">
    <select class="selection" @change="evento => estado.signal = evento.target.value">
      <option class="option" value="sum">+</option>
      <option class="option" value="sub">-</option>
      <option class="option" value="mult">*</option>
      <option class="option" value="division">÷</option>
    </select>
    <h2 class="h-two">Input the second number</h2>
    <input class="input inp-two" type="number" @keyup="evento => estado.n2 = Number(evento.target.value)">
    <div class="answer">
      <h2 class="h-answer">The answer is <span class="answer-span">{{ calculate() }}</span>.</h2>
    </div>
  </div>
</div>
</template>



<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.calculator  {
  width: 640px;
  background-color: #919191;
  margin-top: 120px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 48px 0;
  border-radius: 10px;
}
.input, .selection {
  background-color: white;
  color: black;
  width: 320px;
}

.h-one {
  margin-top: 32px;
}

.h-two {
  margin-top: 32px;
}

.h-one, .h-two {
  border-radius: 10px;
  padding: 9px 9px;
  background-color: #5a5a5a;
}

.input {
  font-size: 32px;
  height: 80px;
}

.selection {
  text-align: center;
  width: 64px;
  height: 40px;
  margin-top: 32px;
  border-radius: 10px;
}

.answer {
  margin-top: 32px;
}

.h-answer {
  margin-top: 8px;
  background-color: #5a5a5a;
  padding: 12px 21px;
  border-radius: 10px;
}

</style>

<style>
* {
  background-color: black;
  color: white;
}
.container, .calculator, .answer, .input, .selection, .answer-span {
  background-color: transparent;
}
</style>