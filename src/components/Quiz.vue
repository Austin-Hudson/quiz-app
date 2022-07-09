<script>
import Question from "@/components/Question.vue";
import Results from "@/components/Results.vue";
import Error from "@/components/ErrorMessage.vue"
import questionsJson from "@/assets/questions.json";

export default {
  name: "Quiz",
  components: { Question, Results, Error },
  props: {
    title: String
  },
  data() {
    return {
      questions: questionsJson,
      displayError: false,
      displayResults: false,
      total: Number,
      totalCorrect: Number
    }
  },
  methods: {
      checkAnswers() {
        let error = 0;
        let correct = 0;
          this.questions.forEach((question, index)=>{
            let answer = this.$refs.question[index].checkAnswer()
            if (answer === undefined){
              error++;
            }
            if(answer === true){
              correct++;
            }
          })
          if(error > 0){
            this.displayError = true;
          }else {
            this.displayError= false;
            this.displayResults = true;

            this.total = this.questions.length;
            this.totalCorrect = correct;
          }
        }
      }
  }

</script>

<template>
  <h1 class="quiz-header"> {{ title }} </h1>
  <Results v-if="displayResults" :total=total :totalCorrect=totalCorrect />
  <div v-for="(quest, index) in questions">
   <Question ref="question" :id=index+1 :question="quest.question"
    :answer="quest.answer" :answers="quest.answers" :showResult=displayResults />
  </div>
  <button class="submit-btn" type="submit" @click.prevent="checkAnswers()">Submit</button>
  <Error v-if="displayError" message="Answer all questions before submitting. Unanswered questions are displayed
  in yellow." />
</template>

<style scoped>
.quiz-header {
  color: #565656;
}
.submit-btn {
  background: #1a721a;
  color: white;
  padding: 8px 15px;
  border-radius: 4px;
}
</style>
