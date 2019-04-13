<template>
  <div>
    <b-nav tabs>
      <b-nav-item disabled><b>Quiz App</b></b-nav-item>
      <b-nav-item>Count: {{numCorrect}}/{{numTotal}}</b-nav-item>

    </b-nav>
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

