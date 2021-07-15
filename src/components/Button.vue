<template>
  <button class="px-3 py-1 bg-gray-800 font-bold rounded-sm">
      {{title}}
  </button>
</template>

<script>
export default {
    name: "Button",
    props: {
        title: {
            type: String,
            default: "Click Here"
        },
    },
}
</script>
