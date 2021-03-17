<template>
  <v-app>
    <v-app-bar app color="pink lighten-3" dark>
<h4>Monthly Budget</h4>
    </v-app-bar>
    <annual-income :annualAmount="annualIncome"/>
  </v-app>
</template>

<script>
import AnnualIncome from './components/AnnualIncome';
export default {
components: { AnnualIncome },
  data() {
    return {
    annualIncome: 0,
    monthlyExpenses: [],  
    }
  }
};
</script>
