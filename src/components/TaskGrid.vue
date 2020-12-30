<template>
  <div class="tasks-grid">
    <template v-if="tasks.length">
      <Task 
        v-for="(task, i) in tasks" 
        :key="task.name" 
        :task="task" 
        @taskDeleted="$emit('taskDeleted', i)" 
        @stateChange="$emit('stateChange', i)"
      />
    </template>
    <p v-else class="no-task">Sua vida está em dia  :)</p>
  </div>
</template>

<script>
import Task from './Task'

export default {
  components: { Task },
  props: {
    tasks: { type: Array, required: true }
  }
}
</script>

<style>
  .tasks-grid {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
  }

  .tasks-grid .task {
    margin: 10px;
  }

  .no-task {
    color: #aaa;
    font-size: 1.7rem;
  }
</style>