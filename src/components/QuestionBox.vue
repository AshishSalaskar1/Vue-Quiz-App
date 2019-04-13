<template>
  <div class="question-box">
    <b-jumbotron>
      <template slot="lead">
        <h5 v-html="currentQuestion.question"></h5>
        <!-- {{currentQuestion.question}} -->
      </template>
      <hr>


      <p>List of answers</p>

      <b-button variant="primary" href="#">Submit</b-button> 
      <b-button @click="next" variant="success" href="#">
        Next
      </b-button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    currentQuestion: Object,
    next: Function
  }
}
</script>

