<template>
  <v-app>
    <v-main class="pa-6 blue-grey lighten-4">
      <v-row justify="center">
        <v-col :cols="12" :md="8" :lg="4">
          <annual-income
            :annualAmount="annualIncome"
            @income-change="handleIncomeChange"
          />
        </v-col>
        <v-col :cols="12" :md="6" :lg="4">
          <income-card title="Monthly Net" :net-amount="monthlyNet" />
        </v-col>
        <v-col :cols="12" :md="6" :lg="4">
          <income-card title="Annual Net" :net-amount="annualNet" />
        </v-col>
      </v-row>
      <v-row>
        <v-col :cols="12" :lg="6">
          <expenses
            :expenses="monthlyExpenses"
            @expense-added="handleExpenseAdded"
            @expense-removed="handleExpenseRemoved"
          />
        </v-col>
        <v-col :cols="12" :lg="6">
          <pie-chart
            :expenses="monthlyExpenses"
            :total-amount="annualExpenses"
          />
        </v-col>
      </v-row>
    </v-main>
  </v-app>
</template>

<script>
import AnnualIncome from "./components/AnnualIncome";
import Expenses from "./components/Expenses";
import IncomeCard from "./components/IncomeCard";
import PieChart from "./components/PieChart";
export default {
  components: { AnnualIncome, Expenses, IncomeCard, PieChart },
  data() {
    return {
      annualIncome: 0,
      monthlyExpenses: []
    };
  },
  created() {
    const presentAnnual = localStorage.getItem("annualIncome");
    const presentExpenses = localStorage.getItem("monthlyExpenses");
    if (presentAnnual) {
      this.annualIncome = parseFloat(presentAnnual);
    }
    if (presentExpenses) {
      this.monthlyExpenses = JSON.parse(presentExpenses);
    }
  },
  methods: {
    handleIncomeChange(income) {
      this.annualIncome = income;
      localStorage.setItem("annualIncome", income);
    },
    handleExpenseAdded(newExpense) {
      this.monthlyExpenses.push(newExpense);
      localStorage.setItem(
        "monthlyExpenses",
        JSON.stringify(this.monthlyExpenses)
      );
    },
    handleExpenseRemoved(expenseToRemove) {
      this.monthlyExpenses = this.monthlyExpenses.filter(e => {
        return e !== expenseToRemove;
      });
      localStorage.setItem(
        "monthlyExpenses",
        JSON.stringify(this.monthlyExpenses)
      );
    }
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
      return this.totalMonthlyExpenses * 12;
    },
    monthlyNet() {
      return (this.monthlyIncome - this.totalMonthlyExpenses).toFixed(2);
    },
    annualNet() {
      return +(this.annualIncome - this.annualExpenses).toFixed(2);
    }
  }
};
</script>