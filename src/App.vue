<template>
  <div id="app">
    <h1 style="text-align:center">Super Quiz</h1>
    <keep-alive>
      <component @switchComponent="questionUp = !questionUp" :is="dynamicComponent"></component>
    </keep-alive>
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
      questionUp: true
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
  }
}
</script>

<style>

</style>
