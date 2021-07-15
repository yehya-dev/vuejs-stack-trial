<template>
  <section class="border-2 p-4">
    <div class="flex justify-between">
      <Header title="Task Manager" />
      <Button
        v-if="$route.path === '/'"
        @click="addTaskOpen = !addTaskOpen"
        :title="addTaskOpen ? 'Close' : 'Add Task'"
        class="text-gray-100"
        :style="{ 'background-color': addTaskOpen ? 'red' : 'green' }"
      />
    </div>
    <router-view :addTaskOpen="addTaskOpen"></router-view>
    <Footer/>
  </section>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import Button from "./components/Button.vue";

export default {
  name: "App",
  components: {
    Header,
    Footer,
    Button,
  },
  data() {
    return {
      tasks: [],
      addTaskOpen: false,
    };
  },
};
</script>

<style></style>
