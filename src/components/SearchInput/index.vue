<template>
  <div class="table__search">
    <input
      type="text"
      v-model="searchTerm"
      placeholder="Rechercher"
      @input="handleSearch"
    />
  </div>
</template>

<script>
export default {
  name: "SearchInput",

  data() {
    return {
      searchTerm: null,
    }
  },

  methods: {
    handleSearch() {
      this.$emit("search", this.searchTerm)
    },
  },
}
</script>

<style lang="scss">
@import 'search-input.scss';
</style>