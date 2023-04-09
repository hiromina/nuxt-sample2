<script setup lang="ts">
type Tweet = {
  id: number;
  description: string;
};

type Props = {
  tweets: Tweet[];
};

defineProps<Props>();

const emit = defineEmits(['delete-tweet']);
const deleteTweet = (id: number) => {
  emit('delete-tweet', id);
}
</script>

<template>
  <li class="tweet-list" v-for="tweet in tweets" :key="tweet.id">
    <span>{{ tweet.description }}</span>
    <button class="delete-button" @click="deleteTweet(tweet.id)">delete</button>
  </li>
</template>

<style scoped>
.tweet-list {
  list-style: none;
  margin-bottom: 12px;
  background-color: aquamarine;
  border-radius: 4px;
  font-size: 12px;
  display: flex;
  justify-content: space-between;
  padding: 8px 20px;
  width: 300px;
}

.delete-button {
  color: gray;
  font-weight: bold;
  background-color: greenyellow;
  border-radius: 2px;
  border: none;
  width: 60px;
  height: 22px;
}

.delete-button:hover {
  background-color: mediumaquamarine;
}
</style>