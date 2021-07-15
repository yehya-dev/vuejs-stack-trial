<template>
  <section class="space-y-1">
    <Task
      @reminder-toggle="$emit('reminder-toggle', task.id)"
      @remove-task="$emit('remove-task', task.id)"
      v-for="task in tasks"
      :key="task.id"
      :task="task"
    />
  </section>
</template>

<script>
import Task from "./Task.vue";

export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
};
</script>
