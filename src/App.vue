<template>
  <div id="app">
    <header>Todo</header>
    <AddTask @add-task="addTask"></AddTask>
    <TaskList :tasks="filteredTasks"></TaskList>
    <Filters :selected-filter="filter" @select-filter="selectFlter"></Filters>
  </div>
</template>

<script>
import AddTask from './components/AddTask.vue'
import TaskList from './components/TaskList.vue'
import Filters from './components/Filters.vue'

let filters = {
  all: function (tasks) {
    return tasks;
  },
  active: function (tasks) {
    return tasks.filter((task) => {
      return !task.completed;
    })
  },
  completed: function (tasks) {
    return tasks.filter((task) => {
      return task.completed;
    })
  }
}

export default {
  name: 'App',
  data: function () {
    return {
      tasks: [],
      filter: 'all'
    }
  },
  components: {
    AddTask,
    TaskList,
    Filters
  },
  methods: {
    addTask (title) {
      this.tasks.push({title: title, completed: false});
    },
    selectFlter(filter) {
      this.filter = filter;
    }
  },
  computed: {
    filteredTasks() {
      return filters[this.filter](this.tasks);
    },
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
