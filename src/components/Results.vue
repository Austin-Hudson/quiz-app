<script>
  export default{
  name: "Results",
  props: {
    total: Number,
    totalCorrect: Number
  },
  data() {
    return {
      percentage: Number
    }
  },
  beforeMount(){
    this.calculatePercentage();
  },
  methods: {
    calculatePercentage(){
        this.percentage = Math.round((100 * this.totalCorrect) / this.total);
    }
  }
}

</script>

<template>
  <div class="results-container">
    <h3 class="results-header">Results</h3>
    <p class="results"> You got {{ totalCorrect }} / {{ total }} questions correct </p>
    <p class="percentage">{{ percentage }}%</p>
  </div>
</template>

<style scoped>
  .results-container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .results-header {
    text-decoration: underline;
  }
  .percentage {
    color: #fe0b0c;
    font-weight: bolder;
  }
  .results, .percentage {
    font-size: 24px;
  }

  @media (max-width: 320px){

    .results-container {
      font-size: 18px;
    }

    .results, .percentage {
      font-size: 18px;
    }
  }
</style>
