<template>
  <div class="p-3 hover:bg-gray-100 cursor-pointer border-b dark:hover:bg-dim-300" :class="wrapperClasses">
    <slot></slot>
  </div>
</template>

<script setup lang="ts">
import {useTailwindConfig} from "../../../../.nuxt/imports";

const { defaultTransition, twitterBorderColor } = useTailwindConfig()

const wrapperClasses = computed(() => `${defaultTransition} ${twitterBorderColor}`)
</script>

<style scoped>

</style>