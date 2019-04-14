<template>
  <div>
    <b-nav tabs>
      <b-nav-item disabled><b><b-h1>Quiz App</b-h1></b></b-nav-item>
      <br>

    </b-nav>
    <br>
      <b-p>
          <h5>Answer Count: {{numCorrect}}/{{numTotal}}</h5>
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

