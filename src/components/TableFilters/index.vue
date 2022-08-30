<template>
  <div class="table__filters" :style="{ top: topPosition }">
    <div
      class="table__filters-item"
      v-for="filter in filters"
      :key="filter._id"
    >
      {{ filter.fr }}
    </div>
  </div>
</template>

<script>
export default {
  name: "TableFilters",

  props: {
    filters: {
      type: Array,
      default: () => [],
    },
  },

  data() {
    return {
      topPosition: null,
    }
  },

  beforeMount() {
    window.addEventListener("scroll", () => {
      this.topPosition = window.scrollY + "px"
    })
  },
}
</script>

<style lang="scss">
@import 'table-filters.scss';
</style>