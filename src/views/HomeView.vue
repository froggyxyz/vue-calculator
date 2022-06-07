<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <CalculatorComponent msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import CalculatorComponent from '@/components/Calculator.vue';

export default {
  name: 'HomeView',
  components: {
    CalculatorComponent,
  },
};
</script>
