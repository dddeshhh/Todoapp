<template>
    <ul class="task-list">
      <li v-for="(task, index) in tasks" :key="index">
        {{task.title}}
      </li>
    </ul>
</template>

<script>

export default {
  name: 'TaskList',
  props: ['tasks'],
  components: {}
}
</script>

<style>
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
