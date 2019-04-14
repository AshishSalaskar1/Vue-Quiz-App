<template>
  <div>
    <b-nav tabs>
      <b-nav-item disabled><b><h2>Quiz App</h2></b></b-nav-item>
      <br>

    </b-nav>
    <br>
      <b-p>
          <h5><b class="score">Your Score: {{numCorrect}}/{{numTotal}} </b></h5>
        </b-p>
  </div> 
</template>


<script>
export default {
  props: [
    'numTotal',
    'numCorrect'
  ]

}
</script>

<style scoped>
.score {
  color: rgb(47, 51, 255);
}
</style>

