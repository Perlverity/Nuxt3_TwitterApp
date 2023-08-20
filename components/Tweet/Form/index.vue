<template>
  <div>

    <div v-if="loading" class="flex items-center justify-center py-6">
      <UISpinner/>
    </div>
    <div v-else>
      <TweetItem :tweet="props.replyTo" v-if="props.replyTo && props.showReply" hideActions/>
      <TweetFormInput :placeholder="props.placeholder" :user="props.user"/>
    </div>

  </div>
</template>

<script setup lang="ts">
const emits = defineEmits(['onSuccess'])
const loading = ref(false)

const props = defineProps({
  user: {
    type: Object,
    required: true
  },
  placeholder: {
    type: String,
    default: "What's happening ?"
  },
  replyTo: {
    type: Object,
    default: null
  },
  showReply: {
    type: Boolean,
    default: false
  }
})


</script>

<style scoped>

</style>