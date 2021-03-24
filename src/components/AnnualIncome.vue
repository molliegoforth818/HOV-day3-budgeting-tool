<template>
  <v-card color="pink lighten-5">
    <v-card-title class="pink--text">Annual Income</v-card-title>
    <v-card-text>
      <v-form @submit.prevent="handleChange">
        <v-text-field
        @blur="handleChange"
          v-model="input"
          type="number"
          outlined
          color="pink"
          filled
          prefix="$"
        />
      </v-form>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  props: ["annualAmount"],
  data() {
    return {
      input: +this.annualAmount,
    };
  },
  methods: {
    handleChange() {
      this.$emit("income-change", +this.input)
      console.log("yo")
    }
  },
};
</script>

<style></style>
