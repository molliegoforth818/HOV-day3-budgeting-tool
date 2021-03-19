<template>
  <v-card height="100%">
    <v-card-title class="pink--text">{{ title }}</v-card-title>
    <v-card-text>
      <h2 class="net-amount pb-5" :class="incomeColor">{{ displayAmount }}</h2>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  props: ["title", "netAmount"],
  computed: {
    displayAmount() {
      return new Intl.NumberFormat("en-US", {
        style: "currency",
        currency: "USD",
      }).format(this.netAmount);
    },
    incomeColor() {
      return {
        "green--text": this.netAmount >= 0,
        "red--text": this.netAmount < 0,
      };
    },
  },
};
</script>

<style scoped>
.net-amount {
  font-size: 4em;
  margin-top: 20px;
  text-align: center;
}
</style>
