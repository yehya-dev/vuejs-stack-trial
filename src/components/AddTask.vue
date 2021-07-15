<template>
  <form
    @submit.prevent="submitForm"
    class="flex flex-col gap-3 border p-4 bg-gray-100 shadow-md"
  >
    <h2 class="font-bold text-xl text-gray-500">Add Task</h2>
    <div class="flex flex-col gap-1">
      <label class="text-sm font-bold text-gray-500" for="task">Task</label>
      <input
        type="text"
        class="px-2 py-1 font-bold text-sm text-gray-500 border"
        placeholder="Add Task"
        v-model="title"
      />
    </div>
    <div class="flex flex-col gap-1">
      <label class="text-sm font-bold text-gray-500" for="desc"
        >Description</label
      >
      <textarea
        id="desc"
        cols="20"
        class="px-2 py-1 font-bold text-sm text-gray-500 border"
        rows="3"
        placeholder="Description"
        v-model="desc"
      ></textarea>
    </div>
    <div class="flex flex-row items-center gap-3">
      <input id="reminder" class="w-5 h-5" v-model="reminder" type="checkbox" />
      <label class="font-bold text-gray-500 select-none" for="reminder"
        >Set Reminder</label
      >
    </div>
    <Button class="text-gray-100 self-end" title="Submit"></Button>
  </form>
</template>

<script>
import Button from "./Button.vue";

export default {
  name: "AddTask",
  components: {
    Button,
  },
  data() {
    return {
      title: "",
      desc: "",
      reminder: false,
    };
  },
  methods: {
    submitForm() {
      if (!(this.title && this.desc)) {
        alert("Please input some data before submitting.");
      } else {
        let newTask = {
          title: this.title,
          desc: this.desc,
          reminder: this.reminder,
        };
        this.$emit("add-task", newTask);
        this.title = "";
        this.desc = "";
        reminder = false;
      }
    },
  },
  emits: ["add-task"],
};
</script>
