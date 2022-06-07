<template>
  <div>
    <div class="display">
      <input v-model.number="operand1" />
      <input v-model.number="operand2" />
      = {{ result }}
    </div>
    <input v-model="fieldNum" type="radio" value="first" name="field" checked />
    <input v-model="fieldNum" type="radio" value="second" name="field" />
    <br />
    <input v-model="isShow" type="checkbox" id="show" name="show" />
    <label for="show">Скрыть/Показать экранную клавиатуру</label>
    <div v-if="isShow" class="keyboard">
      <button
        v-for="operator in operators"
        @click="calculate(operator)"
        :key="operator"
      >
        {{ operator }}
      </button>
      <br />
      <button
        v-for="num in nums"
        @click="
          fieldNum == 'first'
            ? (operand1 = operand1 * 10 + num)
            : (operand2 = operand2 * 10 + num)
        "
        :key="num"
      >
        {{ num }}
      </button>
      <button
        @click="
          fieldNum == 'first'
            ? (operand1 = Math.floor(operand1 / 10))
            : (operand2 = Math.floor(operand2 / 10))
        "
      >
        &#9003;
      </button>
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
      isShow: true,
      fieldNum: 'first',
      operators: ['+', '-', '/', '*', '^', '//'],
      nums: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
    };
  },
  methods: {
    calculate(operator) {
      switch (operator) {
        case '+':
          this.sum(this.operand1, this.operand2);
          break;
        case '-':
          this.dif(this.operand1, this.operand2);
          break;
        case '/':
          this.div(this.operand1, this.operand2);
          break;
        case '*':
          this.multi(this.operand1, this.operand2);
          break;
        case '^':
          this.pow(this.operand1, this.operand2);
          break;
        case '//':
          this.divFloor(this.operand1, this.operand2);
          break;
      }
    },
    sum(operand1, operand2) {
      this.result = operand1 + operand2;
    },
    dif(operand1, operand2) {
      this.result = operand1 - operand2;
    },
    div(operand1, operand2) {
      this.result = operand1 / operand2;
    },
    multi(operand1, operand2) {
      this.result = operand1 * operand2;
    },
    pow(operand1, operand2) {
      this.result = operand1 ** operand2;
    },
    divFloor(operand1, operand2) {
      this.result = Math.floor(operand1 / operand2);
    },
  },
};
</script>
