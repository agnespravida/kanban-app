<template>
    <div>
        <div class="kanban-board">
          <button type="button" class="btn mt-3 mb-3" data-toggle="modal" data-target="#addForm" style="background-color: #5ec0ca; color: white;"  @click="$emit('getCategory', category.id, 'addForm')">Add Task</button>
          <div class="card text-white text-center mb-2 board-title">
            <h1 class="mt-1"style="font-family: 'Russo One', sans-serif;">{{category.name}}</h1>
          </div>
          <div class="card text-white board-body">
            <TaskItem v-for="task in tasks" 
            :key="task.id" 
            v-if="task.categoryName === category.name" 
            :task=task 
            :loggedInEmail=loggedInEmail
            @emitPopulate="emitPopulate"
            @emitMoveTask="emitMoveTask"
            @emitDeleteTask="emitDeleteTask"></TaskItem>
          </div>
        </div>
    </div>
</template>

<script>
import TaskItem from "./TaskItem.vue"
export default {
  name: "TaskBoard",
  data() {
    return {
      taskAdded: {
        CategoryId: null,
        title: null,
        due_date: null
      }
    };
  },
  props: ['category', 'tasks', 'loggedInEmail'],
  components: {
    TaskItem
  },
  methods: {
    emitPopulate(task, page){
      this.$emit('emitPopulate', task, page)  
    },
    emitMoveTask(task, page){
      this.$emit('emitMoveTask', task, page)  
    },
    emitDeleteTask(task){
      console.log(task + " <<< ini dari kanban board")
      this.$emit('emitDeleteTask', task)
    }
  }
};
</script>

<style scoped>
</style>