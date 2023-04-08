<script setup lang="ts">
type Item = {
  value: string;
  isDone: boolean;
};

const items: Item[] = ref([]);
const newItem = ref<string>('');

function addItem(value: string) {
  if(!value) return;
  const itemObj = {
    value: value,
    isDone: false
  }
  items.value.push(itemObj);
  newItem.value = '';
}

function deleteItem() {
  // itemsをrefではなくreactiveにすると上手く動かない。
  items.value = items.value.filter(item => !item.isDone);
}

onUpdated(() => {
  console.log('updated');
});

</script>

<template>
  <Header title="Todo List" />
  <input type="text" v-model="newItem"> <button @click="addItem(newItem)">追加</button>
  <button @click="deleteItem">完了したものを削除</button>
  <table>
    <tr v-for="item in items" :key="item">
      <td :class="{ 'done' : item.isDone }"><input type="checkbox" v-model="item.isDone">{{ item.value }}</td>
    </tr>
  </table>
  <Footer link-to="/sample" link-page="Sample Page" />
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>