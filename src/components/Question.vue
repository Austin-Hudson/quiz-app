<script>
  export default{
    name: "Question",
    props: {
      id: Number,
      question: String,
      answers: Array,
      answer: Number,
      showResult: Boolean
  },
  data() {
    return{
      picked: false,
      isCorrect: false,
      usersChoice: -1,
      submittedAnswer: false
    }
  },
  methods: {
    checkAnswer(){
      this.submittedAnswer = true;
      if(this.picked === false && this.usersChoice === -1) {return undefined}
      if(this.usersChoice === this.answer){
        this.isCorrect = true;
        this.picked = true;
        return true;
      }else {
        this.isCorrect = false;
        this.picked = true;
        return false;
      }
    }
  }

}
</script>

<template>
  <div v-bind:class="{'show-yellow-border' : this.submittedAnswer && !this.picked, 'show-wrong-result' : showResult && !this.isCorrect, 'show-correct-result' : showResult && this.isCorrect }" class="question-container">
    <p>{{id}}. {{ question }}</p>
    <div class="question-div" v-for="(ans, id) in answers" v-bind:class="{'show-correct-answer' : showResult && id === answer && !this.isCorrect }">
      <label class="question-label">
        <input type="radio" :value=id v-model="usersChoice" > {{ ans }}
      </label>
    </div>
    <span v-if="showResult && !this.isCorrect" class="results-text wrong-text">Wrong</span>
    <span v-if="showResult && this.isCorrect" class="results-text correct-text">Correct</span>
  </div>
</template >

<style scoped>
  .question-container {
    box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
    background-color: white;
    height: 175px;
    width: 1200px;
    padding: 10px;
    margin: 15px;
    border-radius: 4px;
    position: relative;

  }
  .show-yellow-border{
    border: 2px solid #FFD700;
  }
  .show-wrong-result {
    border: 2px solid #fd0b0c;
  }
  .show-correct-result {
    border: 2px solid #649664;
  }
  .wrong-text {
    color: #fd0b0c;
  }
  .correct-text {
    color: #649664;
  }
  .show-correct-answer {
    border: 2px solid #006400;
    background: #1a9d1a;
    color: white;
    border-radius: 4px;
    width: 75%;
  }
  .results-text {
    position: absolute;
    bottom: 15px;
    right: 15px;
  }
  .question-div {
    margin: 3px;
    padding: 3px;
  }
  .question-label {
    padding: 4px;
    border-radius: 4px;
  }

  @media (max-width: 1024px){

    .question-container {
      width: 800px;
    }
  }


  @media (max-width: 768px){

    .question-container {
      width: 600px;
    }
  }

  @media (max-width: 320px){

    .question-container {
      width: 300px;
      height: 300px;
      padding: 5px;
      margin: 8px;
    }
  }

</style>
