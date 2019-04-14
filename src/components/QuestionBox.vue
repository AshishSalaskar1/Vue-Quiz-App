<template>
  <div class="question-box">
    <b-jumbotron>
      <template slot="lead">
        <h5 v-html="currentQuestion.question"></h5>
        <!-- {{currentQuestion.question}} -->
      </template>
      <hr>

      <b-list-group>
        <b-list-group-item v-html
          v-for="(answer,index) in shuffledAnswers" 
          :key="index" 
          @click="selectAnswer(index)"
          :class="highlightAnswer(index)">
          {{answer}}
        </b-list-group-item>
      </b-list-group>

      <br>

      <b-button variant="primary"
      @click="submitAnswer"
      :disabled="selectedIndex===null || answered " >
        Submit</b-button> 
      <b-button @click="next" variant="success"
      :disabled="!answered">
        Next
      </b-button>
       <br><br>
       <b><b-h3>{{displayMessage}}</b-h3></b>
    </b-jumbotron>

   
  </div>
</template>

<script>
import _ from 'lodash'

export default {
  props: {
    currentQuestion: Object,
    next: Function,
    increment: Function
  },
  data(){
    return {
      selectedIndex: null,
      shuffledAnswers: [],
      correctIndex: null,
      answered: false,
      displayMessage: ''
    }
  },
  watch: {
    currentQuestion : {
      immediate: true,
      handler(){
        this.selectedIndex = null
        this.shuffleAnswers()
        this.answered = false,
        this.displayMessage = ''
      }
    }
  },
  methods:{
    selectAnswer(index) {
      this.selectedIndex = index
      // console.log(index)
    },
    highlightAnswer(index) {
        let retClass = ''

        if(!this.answered && index === this.selectedIndex){
            retClass = 'selected'
        }
        else if(this.answered && index === this.correctIndex){
          retClass = 'correct'
        }
        else if(this.answered && index === this.selectedIndex && index !== this.correctIndex){
          retClass ='incorrect'
        }
        return retClass
    },
    submitAnswer(){
      let isCorrect = false

      this.displayMessage = "Oops! You were wrong.."
      this.answered = true

      if(this.selectedIndex === this.correctIndex){
        isCorrect = true
        this.displayMessage = "Yes! You got it right!"
      }
 
      this.increment(isCorrect)

    },
    shuffleAnswers(){
      let answers = [...this.currentQuestion.incorrect_answers,this.currentQuestion.correct_answer]
      this.shuffledAnswers = _.shuffle(answers)
      this.correctIndex = this.shuffledAnswers.indexOf(this.currentQuestion.correct_answer)

    }
  },
  computed: {
    Answers() {
      let answers = [...this.currentQuestion.incorrect_answers]
      answers.push(this.currentQuestion.correct_answer)
      return answers;
    }
  }
}
</script>

<style scoped>
.btn {
  margin: 0 10px;
}
.list-group-item:hover {
  background: #EEE;
  cursor: pointer;
}
.selected {
  background-color: rgb(125, 192, 255);
}
.correct{
  background-color: rgb(153, 255, 153);
}
.incorrect{
  background-color: rgb(255, 160, 160);
}
</style>
