<template>
  <div v-if="!isEditable" class="task-view">
    <input type="checkbox" v-model="task.completed"/>
    <label :class="{completed: task.completed}" @dblclick="editTask">{{task.title}}</label>
    <button @click="remove(index)">X</button>
  </div>
  <input v-else=""
  v-model="newTitle"
  class="edit-input"
  @keyup.enter="editDone"
  @keyup.esc="editCancel">
</template>

<script>
export default {
  name: 'Task',
  props: ['task', 'index'],
  data: function () {
    return {
        isEditable: false,
        newTitle: '',
      }
  },
  methods: {
    editTask() {
      this.isEditable = true;
      this.newTitle = this.task.title;
    },
    editDone() {
      this.isEditable = false;
      this.newTitle = this.newTitle.trim();
      if (!this.newTitle) {
        this.remove(this.index);
      } else {
        this.task.title = this.newTitle;
      }
    },
    editCancel() {
      this.isEditable = false;
    },
    complete(e) {
      let completed = e.target.checked;
      this.task.completed = completed;
    },
    remove(index) {
      this.$emit('remove-task', index)
    }
  }
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
.edit-input {
  height: 2em;
  width: 100%;
}

</style>
