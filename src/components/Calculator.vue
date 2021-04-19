<template>
  <div class="calculator">
    <label>List Price</label>
    <input v-model="listPrice" class="input" type="text">
    <label>Down Payment %</label>
    <input v-model="downPaymentPercent" class="input" type="text">
    <label>APR %</label>
    <input v-model="APR" class="input" type="text">
    <label>Lease Length</label>
    <input v-model="leaseLength" class="input" type="text">
    <hr>
    <label>Down Payment</label>
    <input v-model="downPayment" class="output" type="text">
    <label>Car Payment</label>
    <input v-model="monthlyCarPayment" class="output" type="text">
    <label>Yearly Income</label>
    <input v-model="yearlyIncome" class="output" type="text">
    <label>Monthly Income</label>
    <input v-model="monthlyIncome" class="output" type="text">
  </div>
</template>

<script>
export default {
  name: 'Calculator',
  data() {
    return {
      listPrice: 60000,
      downPaymentPercent: 10,
      downPayment: 0,
      APR: 4,
      leaseLength: 48,
      monthlyCarPayment: 0,
      yearlyIncome: 0,
      monthlyIncome: 0
    }
  },
  mounted() {
    this.calculate();
  },
  watch: {
    listPrice: function() {
      this.calculate();
    },
    downPaymentPercent: function() {
      this.calculate();
    },
    APR: function() {
      this.calculate();
    },
    leaseLength: function() {
      this.calculate();
    }
  },
  methods: {
    calculate() {
      this.downPayment = this.listPrice * (this.downPaymentPercent / 100);

      const paymentAfterDownPayment = this.listPrice - this.downPayment;
      const aprAmount = (paymentAfterDownPayment * (this.APR / 100)) / this.leaseLength;
      this.monthlyCarPayment = (paymentAfterDownPayment / this.leaseLength) + aprAmount;

      this.yearlyIncome = (this.monthlyCarPayment * 5) * 12;
      this.monthlyIncome = (this.monthlyCarPayment * 5);
    }
  }
}
</script>

<style>
/* input {
  width: 50%;
} */
</style>