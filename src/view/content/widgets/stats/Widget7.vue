<template>
  <v-card
    class="mt-4 mx-auto"
    max-width="800"
  >
    <v-sheet
      class="v-sheet--offset mx-auto"
      color="cyan"
      elevation="12"
      max-width="calc(100% - 32px)"
    >
      <v-sparkline
        :labels="labels"
        :value="value"
        color="white"
        line-width="2"
        padding="16"
      ></v-sparkline>
    </v-sheet>

    <v-card-text class="pt-0">
      <div class="text-h6 font-weight-light mb-2">
        USER
      </div>
      <div class="subheading font-weight-light grey--text">
        TOTAL SIGN UP
      </div>
      <div class="subheading font-weight-light grey--text">
        SIGN UP THIS MONTH
      </div>
      <v-divider class="my-2"></v-divider>
      <v-card-actions>
        <v-icon
          class="mr-2"
          small
        >
          mdi-clock
        </v-icon>
        <span class="text-caption grey--text font-weight-light">SIGN UP TODAY</span>
      </v-card-actions>
    </v-card-text>
  </v-card>
</template>
<style>
  .v-sheet--offset {
    top: -24px;
    position: relative;
  }
</style>
<script>
  export default {
    data: () => ({
      labels: [
        '12am',
        '3am',
        '6am',
        '9am',
        '12pm',
        '3pm',
        '6pm',
        '9pm',
      ],
      value: [
        100,
        675,
        210,
        790,
        310,
        460,
        550,
        840,
      ],
    }),
  }
</script>
