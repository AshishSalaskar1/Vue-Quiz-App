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
    <!-- //style="display:none" -->
    <div >
        <b-button v-b-modal.modal-1 id="resPopup">Launch demo modal</b-button>
        <!-- Modal Component -->
        <b-modal 
        id="modal-1" 
        centered title="Results"
        :hide-footer="hide-footer">
          <p class="my-4">
            <p id="winText"><b>Thanks for playing</b></p>
            <div id="winScore">
              <br>
              <p id="winText"><b>Your Score is</b></p>
              <h3><b>{{numCorrect}} / {{numTotal}}</b></h3>
              <br>
            </div>
          </p>

          <div slot="modal-footer">
              <b-button @click="playAgain">Play Again</b-button>
          </div>      
        </b-modal>
    </div>
  </div> 



</template>


<script>
export default {
  props: [
    'numTotal',
    'numCorrect',
  ],
  data() {
    return {
      'hide-footer':false
    }
  },
  methods: {
    playAgain(){
       document.location.reload(true);
    },
    gameOver(){
      document.getElementById("resPopup").click();
     
    },
  },
  watch: {
      numTotal : {
        immediate: true,
        handler() {
          if(this.numTotal>9){
            this.gameOver()
          }
        }
      }
  }
}
</script>

<style scoped>
.score {
  color: rgb(47, 51, 255);
}
#winText {
  font-size: 20px;
  color: rgb(199, 0, 50);
}

#winScore {
  background: rgb(189, 222, 255);
  border: 2px solid rgb(0, 58, 112);
  border-radius: 20px;
}
</style>

