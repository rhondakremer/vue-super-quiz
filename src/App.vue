<template>
  <div id="app">
    <h1 style="text-align:center">Super Quiz</h1>
    <transition name="flip" mode="out-in">
    <!-- <keep-alive> -->
      <component @switchComponent="nextQuestion" :is="dynamicComponent" :index="index"></component>
    <!-- </keep-alive> -->
    </transition>
  </div>
</template>

<script>
import Question from './components/Question.vue'
import Correct from './components/Correct.vue'

export default {
  name: 'app',
  components: {
    Question, Correct
  },
  data() {
    return {
      questionUp: true,
      index: 0
    }
  },
  computed: {
    dynamicComponent() {
      if (this.questionUp === true) {
        return Question;
      }
      else {
        return Correct;
      }
    }
  },
  methods: {
    nextQuestion() {
      this.questionUp = !this.questionUp
      if (this.questionUp == false) {
        this.index += 1;
      }
    }
  }
}
</script>

<style>
.flip-enter-active {
  animation: flip-in 1s ease-out forwards;
}

.flip-leave-active {
  animation: flip-out 1s ease-out forwards;
}

@keyframes flip-in {
  from {
    transform: rotateY(90deg);
  }
  to {
    transform: rotateY(0deg)
  }
}

@keyframes flip-out {
  from {
    transform: rotateY(0deg)
  }
  to {
    transform: rotateY(90deg)
  }
}
</style>
