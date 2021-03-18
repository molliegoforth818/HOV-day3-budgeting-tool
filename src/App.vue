<template>
  <v-app>
    <annual-income :annualAmount="annualIncome"/>
    <expenses
    :expenses="monthlyExpenses"
    :total-amount="annualExpenses"
    />
    <income-card title="Monthly Net" :net-amount=-500 />
    <income-card title="Annual Net" :net-amount=500 />
  </v-app>
</template>

<script>
import AnnualIncome from './components/AnnualIncome';
import Expenses from './components/Expenses';
import IncomeCard from './components/IncomeCard'
export default {
components: { AnnualIncome, Expenses, IncomeCard, },
  data() {
    return {
    annualIncome: 0,
    monthlyExpenses: [],  
    }
  }
};
</script>
