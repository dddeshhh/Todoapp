<template lang="html">
    <ul class="task-list">
      <li v-for="(task, index) in tasks" :key="index">
        <Task :task="task" :index="index" @remove-task="removeTask"></Task>
      </li>
    </ul>
</template>

<script>
import Task from './Task.vue';

export default {
  name: 'TaskList',
  props: ['tasks'],
  components: {
    Task
  },
  methods: {
    removeTask(index) {
      this.tasks.splice(index, 1);
    }
  }
}
</script>

<style lang="css">
.task-list {
  margin-left: 0;
  padding: 10px 5px 5px 10px;
  border: 1px solid;
  border-radius: 10px 10px 0px 0px;
  background-color: #FFFACD;
}

li {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
</style>
