<template>
  <div class="table__questions">
    <div v-if="questions.length">
      <div
        class="table__questions-item"
        v-for="question in questions"
        :key="question.id"
      >
        <div class="question-label">
          {{ question.label }}
        </div>
      </div>
    </div>
    <div v-else>No questions available</div>
  </div>
</template>

<script>
export default {
  name: "TableQuestions",

  props: {
    questions: {
      type: Array,
      default: () => [],
    },
  },
}
</script>

<style lang="scss">
@import 'table-questions.scss';
</style>