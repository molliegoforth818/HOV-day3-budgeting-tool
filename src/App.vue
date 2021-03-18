<template>
  <v-app>
    <v-app-bar app color="pink lighten-3" dark>
<h4>Monthly Budget</h4>
    </v-app-bar>
    <annual-income :annualAmount="annualIncome"/>
    <expenses
    :expenses="monthlyExpenses"
    :total-amount="annualExpenses"
    />
  </v-app>
</template>

<script>
import AnnualIncome from './components/AnnualIncome';
import Expenses from './components/Expenses';
export default {
components: { AnnualIncome, Expenses, },
  data() {
    return {
    annualIncome: 0,
    monthlyExpenses: [],  
    }
  }
};
</script>
