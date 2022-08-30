<template>
  <div class="table__scores-container">
    <div v-if="questions.length">
      <div
        class="table__scores"
        v-for="question in questions"
        :key="question.id"
      >
        <div
          class="table__scores-item"
          v-for="score in handleQuestionScores(question.id)"
          :key="score.id"
        >
          <div
            class="score-item"
            :class="handleScoreColor(score.value.toFixed(1))"
          >
            {{ score.value.toFixed(1) }}
          </div>
        </div>
      </div>
    </div>
    <div v-else>No results found</div>
  </div>
</template>

<script>
export default {
  name: "TableFilters",

  props: {
    questions: {
      type: Array,
      default: () => [],
    },

    scores: {
      type: Array,
      default: () => [],
    },
  },

  methods: {
    handleQuestionScores(questionId) {
      return this.scores.find((score) => score.question_id === questionId)
        .scores[0];
    },

    handleScoreColor(score) {
      if (score < 25) {
        return "score__item--red";
      } else if (score >= 25 && score < 50) {
        return "score__item--orange";
      } else if (score >= 50 && score < 75) {
        return "score__item--yellow";
      }

      return "score__item--green";
    },
  },
};
</script>

<style lang="scss">
@import "table-scores.scss";
</style>