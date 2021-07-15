<template>
  <header class="text-gray-700 font-bold text-3xl">
      <h1>{{title}}</h1>
  </header>
</template>

<script>
export default {
    name: 'Header',
    props: {
      title: {
        type: String,
      }
    }
}
</script>
