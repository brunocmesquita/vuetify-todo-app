<template>
  <v-list flat class="pt-0">
    <draggable
      :list="$store.getters.tasksFiltered"
      handle=".handle"
      v-model="tasks"
    >
      <task v-for="task in tasks" :key="task.id" :task="task"></task>
    </draggable>
  </v-list>
</template>

<script>
import draggable from 'vuedraggable';
export default {
  computed: {
    tasks: {
      get() {
        return this.$store.getters.tasksFiltered;
      },
      set(value) {
        this.$store.dispatch('setTasks', value);
      },
    },
  },
  components: {
    task: require('@/components/Todo/Task.vue').default,
    draggable,
  },
};
</script>
