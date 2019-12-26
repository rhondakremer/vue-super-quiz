<template>
  <div id="content" class="col-4 offset-4">
    <p>Good job! Click the button below when you're ready for more</p>
    <button @click="nextQuestion" class="btn btn-primary">Click for next question</button>
  </div>
</template>

<script>
export default {
  methods: {
    nextQuestion(event) {
      this.$emit("switchComponent", event.target.innerHTML);
    }
  }
};
</script>

<style scoped>
#content {
    background-color: pink;
    padding: 10px;
    text-align: center;
    border: 1px solid purple;
}
</style>
