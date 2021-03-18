<template>
  <v-card>
    <v-card-title class="pink--text">Expenses</v-card-title>
    <v-card-text>
      <v-form>
        <v-text-field
          outlined
          label="name"
          v-model="input"
          type="text"
        />
        <v-text-field
          outlined
          label="amount"
          v-model="input"
          type="number"
          prefix="$"
        />
      </v-form>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  props: ["expenses"],
  data() {
    return {
      name: "",
      amount: null,
    };
  },
  methods: {
      handleSubmit(){
        this.$emit("expenses-submitted", { name: this.name, amount: +this.amount});   
      }
  }
};
</script>

<style></style>
