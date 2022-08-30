<template>
  <div id="app">
    <Table
      :filters="tableFilters"
      :questions="tableQuestions"
      :scores="tableScores"
    />
  </div>
</template>

<script>
import filters from "./assets/json/filters.json"
import questions from "./assets/json/questions.json"
import scores from "./assets/json/scores.json"

import Table from "./components/Table.vue"

export default {
  name: "App",
  components: {
    Table,
  },
  data() {
    return {
      tableFilters: filters,
      tableQuestions: questions,
      tableScores: scores,
    }
  },
}
</script>

<style lang="scss">
* {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>