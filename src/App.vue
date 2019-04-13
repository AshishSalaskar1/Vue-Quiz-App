<template>
  <div id="app">
    <Header/><br><br>
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3"> <QuestionBox/> </b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script>

import Header from './components/Header.vue'
import QuestionBox from './components/QuestionBox.vue'

export default {
  name: 'app',
  components: {
    Header,
    QuestionBox
  },
  data(){
    return {
      questions: []
    }
  },
  mounted: function(){
    fetch("https://opentdb.com/api.php?amount=10&type=multiple",{
      method: 'get'
    })
    .then((res) => res.json())
    .then((data) => {
        this.questions = data.results
    })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
