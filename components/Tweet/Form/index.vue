<template>
  <div>
    <TweetFormInput :user="props.user" />
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  user: {
    type: Object,
    required: true
  }
})
</script>

<style scoped>

</style>