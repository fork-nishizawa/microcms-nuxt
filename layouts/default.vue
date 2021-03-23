<template lang="pug">
  v-app(light)
    v-main.pt-8
      v-container
        nuxt
    v-footer(:absolute="!fixed" app)
      span
        |&copy; {{ new Date().getFullYear() }}
</template>

<script>
export default {
  data() {
    return {
      fixed: false,
    }
  },
}
</script>
