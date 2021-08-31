<template>
  <v-dialog :value="true" persistent max-width="290">
    <v-card>
      <v-card-title class="headline">
        Edit task
      </v-card-title>
      <v-card-text
        >Edit the title of this task:
        <v-text-field @keyup.enter="saveTask" v-model="taskTitle">
        </v-text-field
      ></v-card-text>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn @click="$emit('close')" text>
          Cancel
        </v-btn>
        <v-btn
          :disabled="taskTitleInvalid"
          @click="saveTask"
          color="red darken-1"
          text
        >
          Save
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  props: ['task'],
  computed: {
    taskTitleInvalid() {
      return !this.taskTitle || this.taskTitle === this.task.title;
    },
  },
  data() {
    return {
      taskTitle: null,
    };
  },
  methods: {
    saveTask() {
      if (!this.taskTitleInvalid) {
        let payload = {
          id: this.task.id,
          title: this.taskTitle,
        };
        this.$store.dispatch('updateTaskTitle', payload);
        this.$emit('close');
      }
    },
  },
  mounted() {
    this.taskTitle = this.task.title;
  },
};
</script>

<style></style>
