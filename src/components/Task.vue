<template>
  <div
    class="shadow-md bg-gray-100 relative p-1"
    :class="{ 'border-l-8 border-green-400': task.reminder }"
  >
    <h1 class="font-bold text-lg text-gray-600 px-3">{{ task.title }}</h1>
    <p class="text-gray-500 font-bold text-xs px-5 py-1"> - {{ task.desc }}</p>
    <button
      @click="$emit('remove-task', task.id)"
      class="absolute top-2 right-2 text-red-400"
    >
      <i class="fas fa-times-circle text-xl" aria-hidden="true"></i>
    </button>
    <button
      @click="$emit('reminder-toggle', task.id)"
      class="absolute top-2 right-9 text-green-400"
    >
      <i class="fas fa-plus-square text-xl"></i>
    </button>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  emits: ["remove-task", "reminder-toggle"],
};
</script>
