<template>
  <div>
    <div class="display">
      <input v-model="operand1" />
      <input v-model="operand2" />
      = {{ result }}
    </div>
    <div class="keyboard">
      <button @click="sum(operand1, operand2)">+</button>
      <button @click="dif(operand1, operand2)">-</button>
      <button @click="div(operand1, operand2)">/</button>
      <button @click="multi(operand1, operand2)">*</button>
      <button @click="pow(operand1, operand2)">^</button>
      <button @click="divFloor(operand1, operand2)">//</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CalculatorComponent',
  data() {
    return {
      operand1: 0,
      operand2: 0,
      result: 0,
    };
  },
  methods: {
    sum(operand1, operand2) {
      this.result = Number(operand1) + Number(operand2);
    },
    dif(operand1, operand2) {
      this.result = Number(operand1) - Number(operand2);
    },
    div(operand1, operand2) {
      this.result = Number(operand1) / Number(operand2);
    },
    multi(operand1, operand2) {
      this.result = Number(operand1) * Number(operand2);
    },
    pow(operand1, operand2) {
      this.result = Number(operand1) ** Number(operand2);
    },
    divFloor(operand1, operand2) {
      this.result = Math.floor(Number(operand1) / Number(operand2));
    },
  },
};
</script>
