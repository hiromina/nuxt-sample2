<script setup lang="ts">
const tweets = ref([{id: 1, description: 'Hello!'}]);
const inputtingDescription = ref<string>('');

const postTweet = () => {
  const tweet = {id: Math.random(), description: inputtingDescription.value};
  tweets.value.push(tweet);
  inputtingDescription.value = '';
}

const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter(t => t.id !== id);
}

</script>

<template>
  <div class="container">
    <h1>Tweet</h1>
    <div class="form-container">
      <input v-model="inputtingDescription" />
      <button class="save-button" @click="postTweet">post</button>
    </div>
    <div class="tweet-container">
      <p v-show="tweets.length <= 0">No data.</p>
      <ul>
        <li class="tweet-list" v-for="tweet in tweets" :key="tweet.id">
          <span>{{ tweet.description }}</span>
          <button class="delete-button" @click="deleteTweet(tweet.id)">delete</button>
        </li>
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

.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: aliceblue;
  padding: 24px 0;
  width: 60%;
  margin-bottom: 12px;
  border-radius: 4px;
}

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

.save-button {
  color: #fff;
  font-weight: bold;
  background-color: #68c9c9;
  border-radius: 2px;
  border: none;
  width: 60px;
  height: 22px;
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

.save-button:hover {
  background-color: #37bdbd;
}

.delete-button:hover {
  background-color: mediumaquamarine;
}

input {
  margin-bottom: 16px;
}

</style>