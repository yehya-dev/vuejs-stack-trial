<template>
  <footer class="text-center p-3">
      <router-link v-if="this.$route.path === '/'" class="text-blue-700" to="/about">About</router-link>
      <router-link v-else-if="this.$route.path === '/about'" class="text-blue-700" to="/">Home</router-link>
  </footer>
</template>



