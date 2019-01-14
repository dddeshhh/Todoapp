<template lang="html">
  <div class="filters">
    <span v-for="(filter, index) in filters"
      :key="index"
      @click="selectFilter(filter)">
      {{filter}}</span>
  </div>
</template>

<script>
export default {
  name: 'Filters',
  propd: ['selectedFilter'],
  data: function () {
    return {
      filters: [
        'all',
        'active',
        'completed'
      ],
      selected: 'all'
    }
  },
  methods: {
    selectFilter(filter) {
      this.$emit('select-filter', filter);
      this.selected = filter;
    },
    isSelected() {
      return this.selectedFilter === filter;
    }
  },
}
</script>

<style lang="css">
  .filters {
    margin-top: 20px;
  }
  .filters span {
    margin: 2px;
    padding: 5px;
    border: 1px solid;
    border-radius: 5px;
    cursor: pointer;
  }
</style>
