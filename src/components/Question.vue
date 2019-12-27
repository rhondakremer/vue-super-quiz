<template>
  <div>
    <div id="questions" v-if="!gameOver" class="col-4 offset-4">
    <h4 style="text-align:center">{{ questions[index].question}}</h4>
    <ul>
      <li v-for="(answer,index) in questions[index].answers" :key="index" @click="checkAnswer" class="col-4 offset-4">{{ answer }}</li>
    </ul>
    </div>
    <transition enter-active-class="animated zoomOutDown">
    <div v-if="gameOver" style="text-align: center">
      Game over! A+
    </div>
    </transition>
   

  </div>
</template>

<script>
export default {
  data() {
    return {
      questions: [
        {question: "What is a duck?", answers: ["Potato", "Muffin", "Walrus", "Predator"], correct: "Potato"},
        {question: "How many people?", answers: ["1", "2", "3", "4"], correct: "2"}
      ],
      // current: 0,
      gameOver: false
    }
  },
  methods: {
    checkAnswer(event) {
      if (event.target.innerText === this.questions[this.$props.index].correct) {
        // this.current += 1;
        this.gameOverCheck()
      }
      else {
        alert("No, try again!")
      }
    },
    gameOverCheck() {
    if (this.index == this.questions.length - 1) {
      this.gameOver = true;
    }
    else {
      this.$emit("switchComponent", event.target.innerHTML)
    }
  }
  },
  props: ["index"]
}
</script>

<style scoped>
#questions {
  background-color: #98ff98;
  border: 1px solid brown;

}
</style>
