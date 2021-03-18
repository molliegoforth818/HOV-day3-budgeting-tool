<template>
  <v-card>
    <v-card-title class="pink--text">Annual Income</v-card-title>
    <v-card-text>
      <v-form>
        <v-text-field
          outlined
          label="annualIncome"
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
  props: ["annualAmount"],
  data() {
    return {
      input: +this.annualAmount,
    };
  },
  methods: {},
};
</script>

<style></style>
