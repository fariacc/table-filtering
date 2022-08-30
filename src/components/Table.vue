<template>
  <div class="table">
    <div class="table__left-container">
      <SearchInput @search="handleSearch" />
      <TableQuestions :questions="filteredQuestions" />
    </div>
    <div class="table__right-container">
      <TableFilters :filters="filters" />
      <TableScores :questions="filteredQuestions" :scores="scores" />
    </div>
  </div>
</template>

<script>
import SearchInput from "./SearchInput";
import TableQuestions from "./TableQuestions";
import TableFilters from "./TableFilters";
import TableScores from "./TableScores";

export default {
  name: "Table",

  // not importing the json files in this table component
  // to follow the concept of implementing reusable components
  // so i'm passing as props instead

  props: {
    filters: {
      type: Array,
      default: () => [],
    },
    questions: {
      type: Array,
      default: () => [],
    },
    scores: {
      type: Array,
      default: () => [],
    },
  },

  components: {
    SearchInput,
    TableQuestions,
    TableFilters,
    TableScores,
  },

  data() {
    return {
      filteredQuestions: [],
    };
  },

  computed: {
    formattedQuestions() {
      return this.questions.map((question) => {
        return {
          label: question.labels.fr,
          id: question._id,
        };
      });
    },
  },

  mounted() {
    this.filteredQuestions = this.formattedQuestions;
  },

  methods: {
    handleSearch(term) {
      if (term) {
        this.filteredQuestions = this.formattedQuestions.filter((question) =>
          question.label.toLowerCase().includes(term.toLowerCase())
        );
      } else {
        this.filteredQuestions = this.formattedQuestions;
      }
    },
  },
};
</script>

<style lang="scss">
.table {
  color: #52616e;
  display: flex;
}

.table__left-container {
  min-width: 400px;
  border-right: 1px solid #eaeaea;
  max-width: 400px;
}

.table__right-container {
  overflow-x: auto;
  width: 100%;
  flex: auto;
  position: relative;
}
</style>