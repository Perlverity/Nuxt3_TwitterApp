<template>
  <div>
    <MainSection title="Home" :loading="loading">
      <TweetForm :user="user"/>
      <TweetListFeed :tweets="homeTweets" />
    </MainSection>
  </div>
</template>

<script setup lang="ts">
const loading = ref(false)
const user = ref(
  {
    name: 'ぱーる',
    handle: '@perlverity',
    image: 'https://picsum.photos/200/200'
  }
)
</script>

<style scoped>

</style>