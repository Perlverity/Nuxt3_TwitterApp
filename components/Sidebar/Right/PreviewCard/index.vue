<template>
  <div class="m-2 overflow-hidden border rounded-2xl bg-gray-50 dark:bg-dim-700" :class="twitterBorderColor">
    <h1 class="p-3 text-xl font-extrabold text-gray-900 border-b dark:text-white" :class="twitterBorderColor">
      {{ props.title }}
    </h1>

    <slot></slot>

    <div class="p-3 text-sm text-blue-400 cursor-pointer hover:bg-gray-100 dark:hover:bg-dim-300" :class="defaultTransition">
      さらに表示
    </div>
  </div>
</template>

<script setup lang="ts">
import { useTailwindConfig } from "../../../../.nuxt/imports";

const { twitterBorderColor, defaultTransition } = useTailwindConfig()

const props = defineProps({
  title: {
    type: String,
    required: true
  }
})
</script>

<style scoped>

</style>