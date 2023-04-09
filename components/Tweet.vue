<script setup lang="ts">
const tweets = ref([{id: 1, description: 'Hello!'}]);

const postTweet = (description: string) => {
  const tweet = {id: Math.random(), description};
  tweets.value.push(tweet);
}

const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter(t => t.id !== id);
}

</script>

<template>
  <div class="container">
    <h1>Tweet</h1>
    <TweetPostForm @post-tweet="postTweet" />
    <div class="tweet-container">
      <p v-show="tweets.length <= 0">No data.</p>
      <ul>
        <TweetListItem :tweets="tweets" @delete-tweet="deleteTweet" />
      </ul>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

</style>