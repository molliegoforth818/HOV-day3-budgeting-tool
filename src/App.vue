<template>
  <v-app>
    <annual-income :annualAmount="annualIncome" />
    <expenses :expenses="monthlyExpenses" :total-amount="annualExpenses" />
    <income-card title="Monthly Net" :net-amount="monthlyNet" />
    <income-card title="Annual Net" :net-amount="annualNet" />
  </v-app>
</template>

<script>
import AnnualIncome from "./components/AnnualIncome";
import Expenses from "./components/Expenses";
import IncomeCard from "./components/IncomeCard";
export default {
  components: { AnnualIncome, Expenses, IncomeCard },
  data() {
    return {
      annualIncome: 0,
      monthlyExpenses: [],
    };
  },
  computed: {
    monthlyIncome() {
      return this.annualIncome / 12;
    },
    totalMonthlyExpenses() {
      return this.monthlyExpenses.reduce((total, month) => {
        return total + month.amount;
      }, 0);
    },
    annualExpenses() {
      return this.monthlyExpenses * 12;
    },
    monthlyNet() {
      return (this.monthlyIncome - this.totalMonthlyExpenses)
    },
    annualNet() {
      return +(this.annualIncome - this.annualExpenses)
    }
  },
};
</script>
