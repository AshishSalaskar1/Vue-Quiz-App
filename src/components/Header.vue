<template>
  <div>
    <b-nav tabs>
      <b-nav-item disabled><b><h2>Quiz App</h2></b></b-nav-item>
      <br>

    </b-nav>
    <br>
      <b-p>
          <b-h2><b>Your Score: {{numCorrect}}/{{numTotal}} </b></b-h2>
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

