<template>
  <div>


    <TweetItemHeader :tweet="props.tweet"/>


    <div :class="tweetBodyWrapper" v-for="tweetItem in tweetItems">
      <p class="flex-shrink w-auto font-medium text-gray-800 dark:text-white" :class="textSize">
        {{ tweetItem.content }}
      </p>

      <div v-for="image in tweet.mediaFiles" :key="image.id" class="flex my-3 mr-2 border-2 rounded-2xl"
           :class="twitterBorderColor">
        <img :src="tweetItem.image" class="w-full rounded-2xl"/>
      </div>


      <div class="mt-2" v-if="!props.hideActions">
        <TweetItemActions :tweet="props.tweet" :compact="props.compact"
                          @on-comment-click="handleCommentClick"/>
      </div>

    </div>


  </div>
</template>
<script setup>
const {twitterBorderColor} = useTailwindConfig()

const emitter = useEmitter()

const props = defineProps({
  tweet: {
    type: Object,
    required: true
  },
  compact: {
    type: Boolean,
    default: false
  },
  hideActions: {
    type: Boolean,
    default: false
  }
})

const tweetBodyWrapper = computed(() => props.compact ? 'ml-16' : 'ml-2 mt-4')

const textSize = computed(() => props.compact ? 'text-base' : 'text-2xl')

function handleCommentClick () {
  emitter.$emit('replyTweet', props.tweet)
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

</script>