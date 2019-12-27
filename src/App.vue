<template>
  <div id="app">
    <h1 style="text-align:center">Super Quiz</h1>
    <transition enter-active-class="animated flipInX" leave-active-class="animated flipOutY" mode="out-in">
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
.slide-enter {
  opacity: 0;
}

.slide-enter-active {
  animation: slide-in 1s ease-out forwards;
  transition: opacity 1s;
}

.slide-leave-to {
  opacity: 0;
}

.slide-leave-active {
  animation: slide-out 1s ease-out forwards;
  transition: opacity 1s;
}

@keyframes slide-in {
  from {
    transform: translateX(90%);
  }
  to {
    transform: translateX(O)
  }
}

@keyframes slide-out {
  from {
    transform: translateX(0)
  }
  to {
    transform: translateX(90%)
  }
}
</style>
