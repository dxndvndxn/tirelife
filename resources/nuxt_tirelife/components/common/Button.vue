<template>
  <button class="btn red-bg" :class="[width, fz]">
    {{ word }}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: ['width', 'fz', 'word']
}
</script>

<style scoped>

</style>
