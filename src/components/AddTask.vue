<template lang="html">
  <div class="add-task">
    <input v-model="title" autofocus/>
    <button @click="addTask">add new task</button>
  </div>
</template>

<script>
export default {
  name: 'AddTask',
  data: function () {
    return {
      title: ''
    }
  },
  methods: {
    addTask () {
      this.$emit('add-task', this.title);
      this.title = '';
    }
  }
}
</script>

<style lang="css">
  .add-task input {
    display: inline-table;
    border-radius: 10px;
    height: 2em;
    width: 100%;
  }
  .add-task button {
    height: 2em;
    border: 0;
    border-radius: 5px;
    background-color: #3CB371;
  }
</style>
