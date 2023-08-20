<template>
  <div>
    <TweetItemHeader :tweet="props.tweet"/>


    <div class="p-4 border-b" :class="twitterBorderColor" v-for="tweetItem in tweetItems">
      <div class="flex">
        <img :src="tweetItem.image" class="w-10 h-10 rounded-full"/>
        <div class="ml-3">
          <span class="font-medium text-gray-800 dark:text-white">{{ tweetItem.name }}</span>
        </div>
        <div class="ml-3 text-sm font-medium text-gray-400">
          @perlverity
          ・14 時間前
        </div>
      </div>
      <p class="flex-shrink w-auto font-medium text-gray-800 dark:text-white" :class="textSize">
        {{ tweetItem.content }}
      </p>

      <img :src="tweetItem.image" class="my-5 h-full border-2 rounded-2xl"/>

      <div class="flex items-center justify-around w-full">

        <TweetItemActionsIcon color="blue" @on-click="emits('onCommentClick')" :size="size">

          <template v-slot:icon="{ classes }">
            <div class="flex">
            <ChatBubbleBottomCenterIcon :class="classes"/>
              <div class="px-3">
                <span>1</span>
              </div>
            </div>

          </template>


        </TweetItemActionsIcon>

        <TweetItemActionsIcon color="green" :size="size">

          <template v-slot:icon="{ classes }">
            <div class="flex">
            <ArrowPathRoundedSquareIcon :class="classes"/>
              <div class="px-3">
                <span>1</span>
              </div>
            </div>

          </template>

        </TweetItemActionsIcon>


        <TweetItemActionsIcon color="red" :size="size">

          <template v-slot:icon="{ classes }">
            <div class="flex">
            <HeartIcon :class="classes"/>
              <div class="px-3">
                <span>5</span>
              </div>
            </div>

          </template>

        </TweetItemActionsIcon>

        <TweetItemActionsIcon color="blue" :size="size">

          <template v-slot:icon="{ classes }">
            <ListBulletIcon :class="classes"/>
          </template>

          <template v-if="showStats" v-slot:default>
            {{ generateRandomNumber() }}
          </template>

        </TweetItemActionsIcon>

      </div>

    </div>


  </div>
</template>

<script setup lang="ts">
const {twitterBorderColor, defaultTransition} = useTailwindConfig()

const props = defineProps({
  tweets: {
    type: Array,
    required: true
  }
})

function redirect(tweet) {
  navigateTo(`/status/${tweet.id}`)
}

const tweetItems = ref([
  {
    name: 'ぱーる',
    content: '約3年前。頑張ったなお主。',
    image: 'https://picsum.photos/200/200'
  },
  {
    name: 'ぱーる',
    content: 'もう少しで最低限の機能の実装は終わりそう！',
    image: 'https://picsum.photos/200/200'
  },
  {
    name: 'ぱーる',
    content: '初ツイート。',
    image: 'https://picsum.photos/200/200'
  },
])

import { ChatBubbleBottomCenterIcon, ArrowPathRoundedSquareIcon, HeartIcon, ListBulletIcon } from '@heroicons/vue/24/outline'

const emits = defineEmits(['onCommentClick'])


const showStats = computed(() => props.compact)
const size = computed(() => props.compact ? 5 : 8)

function generateRandomNumber() {
    return Math.floor(Math.random() * 100)
}
</script>

<style scoped>

</style>