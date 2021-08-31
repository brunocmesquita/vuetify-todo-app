<template>
  <v-list flat class="pt-0">
    <task
      v-for="task in $store.getters.tasksFiltered"
      :key="task.id"
      :task="task"
    ></task>
  </v-list>
</template>

<script>
import Task from './Task.vue';
export default {
  components: {
    task: require('@/components/Todo/Task.vue').default,
  },
};
Task;
</script>
