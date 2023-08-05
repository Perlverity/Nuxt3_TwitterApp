<template>
  <div class="flex flex-col">
    <!--  プレビューカード  -->
    <div>
      <SidebarRightPreviewCard title="いまどうしてる？">

        <SidebarRightPreviewCardItem v-for="whatsHappening in whatsHappeningItems">
          <div>
            <h2 class="font-bold text-gray-800 text-md dark:text-white"> {{ whatsHappening.title }}</h2>
            <p class="text-xs text-gray-400"> {{ whatsHappening.count }}</p>
          </div>
        </SidebarRightPreviewCardItem>
      </SidebarRightPreviewCard>
    </div>
    <!--  プレビューカード  -->
    <div>
      <SidebarRightPreviewCard title="誰をフォローする">
        <SidebarRightPreviewCardItem v-for="whoToFollow in whoToFollowItems">
          <div class="flex flex-row justify-between p-2">
            <div class="flex flex-row">
              <img :src="whoToFollow.image" :alt="whoToFollow.name" class="w-10 h-10 rounded-full">
              <div class="flex flex-col ml-2">
                <h1 class="text-sm font-bold text-gray-900 dark:text-white"> {{ whoToFollow.name }}</h1>
                <p> {{ whoToFollow.handle }}</p>
              </div>
            </div>
            <div class="flex h-full">
              <button class="px-4 py-2 text-xs font-bold text-white bg-black dark:text-black dark:bg-white rounded-full">フォロー</button>
            </div>
          </div>
        </SidebarRightPreviewCardItem>
      </SidebarRightPreviewCard>
    </div>
  </div>
</template>

<script setup lang="ts">

const whatsHappeningItems = ref([
  {
    title: 'SpaceX',
    count: '18.8k Tweets'
  },
  {
    title: '#Coding',
    count: '8.8k Tweets'
  },
  {
    title: '#fun',
    count: '18.8k Tweets'
  }
])

const whoToFollowItems = ref([
  {
    name: 'ぱーる',
    handle: '@perlverity',
    image: 'https://picsum.photos/200/200'
  },
 {
    name: 'ぱーる',
    handle: '@perlverity',
    image: 'https://picsum.photos/200/200'
  },
  {
    name: 'ぱーる',
    handle: '@perlverity',
    image: 'https://picsum.photos/200/200'
  },
])

</script>

<style scoped>

</style>