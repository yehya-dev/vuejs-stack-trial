<template>
  <AddTask v-if="addTaskOpen" @add-task="addTask" class="mt-4" />
  <Tasks
    @remove-task="deleteTask"
    @reminder-toggle="reminderToggle"
    class="my-2"
    :tasks="tasks"
  />
</template>

<script>
import Tasks from "../components/Tasks.vue";
import AddTask from "../components/AddTask.vue";

export default {
  name: "Home",
  components: {
    Tasks,
    AddTask,
  },
  props: {
      addTaskOpen: Boolean
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    async deleteTask(taskid) {
      let resp = await fetch(`/api/${taskid}`, {
        method: "DELETE",
      });
      if (resp.status == 200) {
        this.tasks = this.tasks.filter((value) => value.id !== taskid);
      } else {
        alert("The Task couldn't be deleted");
      }
    },
    async reminderToggle(taskid) {
      let taskToChangeIndex = this.tasks.findIndex(
        (task) => task.id === taskid
      );
      let ChangeReminder = !this.tasks[taskToChangeIndex].reminder;

      let resp = await fetch(`/api/${taskid}`, {
        method: "PATCH",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({ reminder: ChangeReminder }),
      });

      let response_data = await resp.json();

      this.tasks[taskToChangeIndex] = response_data;
    },
    async addTask(data) {
      let newId =
        this.tasks.length == 0 ? 0 : this.tasks[this.tasks.length - 1].id + 1;
      let newTask = { id: newId, ...data };

      let resp = await fetch("/api/", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(newTask),
      });

      let obj_data = await resp.json();

      this.tasks = [...this.tasks, obj_data];
    },
    async getAllTasks() {
      let res = await fetch("/api");
      let data = await res.json();
      this.tasks = data;
    },
  },
  async created() {
    this.getAllTasks();
  },
};
</script>

<style></style>
