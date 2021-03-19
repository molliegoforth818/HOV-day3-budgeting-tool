<template>
<v-card height="100%">
    <v-vard-title class="pink--text">Monthly Expenses</v-vard-title>
<apexchart type="pie" :options="options" :series="series" height="300">
</v-card>
</template>

<script>
export default {
  props: ["expenses", "totalAmount"],
  computed: {
    series() {
       return this.expenses.map(expenses => expenses.amount); 
    },
    options() {
        return {
            labels: this.expenses.map(expenses => expenses.name)
        }
    }
  }
};
</script>

<style></style>
