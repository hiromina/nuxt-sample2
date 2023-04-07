<script setup lang="ts">
type Item = {
  value: string;
  isDone: boolean;
};

let items: Item[] = reactive([]);
let newItem = '';

function addItem(value: string) {
  if(!value) return;
  const itemObj = {
    value: value,
    isDone: false
  }
  items.push(itemObj);
  newItem = '';
}

function deleteItem() {
  // TODO 上手く動かない。
  // チェックを付ける →削除ボタンを押しても削除されない →削除対象のチェックを外そうとクリックすると、やっと画面から消える。
  items = items.filter(item => !item.isDone);
  console.log('削除');
}
</script>

<template>
  <Header title="Todo List" />
  <input type="text" v-model="newItem"> <button @click="addItem(newItem)">追加</button>
  <button @click="deleteItem">完了したものを削除</button>
  <table>
    <tr v-for="item in items">
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