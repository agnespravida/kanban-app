<template>
  <div class="card text-white mt-3 board-items">
    <div class="card-header">
      <button type="button" class="close" data-dismiss="alert" aria-label="Close" v-if="task.createdBy === loggedInEmail" @click="$emit('emitDeleteTask', task)">
          <span aria-hidden="true">&times;</span>
      </button>
      <p><strong>{{task.name}}</strong></p>
      <button type="button" class="btn" data-toggle="modal" data-target="#editForm" style="background-color: white; color: #5ec0ca;" 
      v-if="task.createdBy === loggedInEmail"
      @click="$emit('emitPopulate', task, 'editForm')">Edit</button>
      <button type="button" class="btn" data-toggle="modal" data-target="#moveForm" style="background-color: white; color: #5ec0ca;" 
      v-if="task.createdBy === loggedInEmail"
      @click="$emit('emitMoveTask', task, 'moveForm')">Move</button>
    </div>
    <div class="card-body">
      <p>Due Date: {{task.converted_due_date}}<br>Created By: {{task.createdBy}}</p>
    </div>
  </div>
</template>

<script>
name: "TaskItem"
export default {
  data() {
    return {
    };
  },
  props: ['task', 'loggedInEmail']
};
</script>

<style scoped>
</style>