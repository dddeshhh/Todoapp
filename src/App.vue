<template>
  <div id="app">
    <header>Todo</header>
    <AddTask @add-task="addTask"></AddTask>
    <TaskList :tasks="tasks"></TaskList>
  </div>
</template>

<script>
import AddTask from './components/AddTask.vue'
import TaskList from './components/TaskList.vue';

export default {
  name: 'App',
  data: function () {
    return {
      tasks: []
    }
  },
  components: {
    AddTask,
    TaskList
  },
  methods: {
    addTask (title) {
      this.tasks.push({title: title, completed: false});
    }
  },
}
</script>

<style>
  body {
    margin-left: 30%;
  }
  header {
    font-size: 8em;
    text-shadow: 1px 1px 2px black, 0 0 1em green;
  }
  #app {
    max-width: 300px;
  }
</style>
