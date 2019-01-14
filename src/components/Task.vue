<template>
  <div class="task-view">
    <input type="checkbox"/>
    <label>{{task.title}}</label>
    <button>X</button>
  </div>
</template>

<script>
export default {
  name: 'Task',
  props: ['task', 'index'],
}
</script>

<style lang="css">
.completed {
  text-decoration: line-through;
}
.task-view {
  display: flex;
  margin-top: 5px;
  height: 2em;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  border: 1px solid cornflowerblue;
  border-radius: 5px;
  border-color: green;
  background-color: white;
}
.task-view button {
  margin: 0;
  border: 0;
  background: none;
  margin-left: auto;
}
.task-view label {
  word-break: break-all;
}

</style>
