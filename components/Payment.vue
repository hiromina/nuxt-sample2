<script setup lang="ts">
type Item = {
  name: string;
  price: number;
  url: string;
};
const items: Item[] = ref([
    {
      name: 'Desk',
      price: 40000,
      url: 'https://www.amazon.co.jp/Amazon%E3%83%99%E3%83%BC%E3%82%B7%E3%83%83%E3%82%AF-%E3%83%91%E3%82%BD%E3%82%B3%E3%83%B3%E3%83%87%E3%82%B9%E3%82%AF-%E3%83%96%E3%83%A9%E3%83%83%E3%82%AF-%E5%B9%85120%C3%97%E5%A5%A5%E8%A1%8C55x%E9%AB%98%E3%81%9560-80cm/dp/B09PHXBXT2/ref=sr_1_1_sspa?keywords=%E3%83%87%E3%82%B9%E3%82%AF&qid=1680833997&sr=8-1-spons&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUFFR1dUOERTVFAyMFkmZW5jcnlwdGVkSWQ9QTAwMjYxODQxSENZUTJERk01Q1ExJmVuY3J5cHRlZEFkSWQ9QTMyOTIyREk2NTRMSzUmd2lkZ2V0TmFtZT1zcF9hdGYmYWN0aW9uPWNsaWNrUmVkaXJlY3QmZG9Ob3RMb2dDbGljaz10cnVl&th=1'
    },
  {
    name: 'Bike',
    price: 20000,
    url: 'https://www.amazon.co.jp/dp/B07CXM6NBK/ref=redir_mobile_desktop?_encoding=UTF8&aaxitk=5ab3acca9fd9ba578951d396d57263a5&content-id=amzn1.sym.940fa71d-7f78-44a7-86e7-0cc4901f1d5f%3Aamzn1.sym.940fa71d-7f78-44a7-86e7-0cc4901f1d5f&hsa_cr_id=6794613780203&pd_rd_plhdr=t&pd_rd_r=7e4028fd-048a-4db7-8c16-22a3a4441718&pd_rd_w=rNCBM&pd_rd_wg=vPUbE&qid=1680834037&ref_=sbx_be_s_sparkle_lsi4d_asin_0_title&sr=1-1-ac08f2b1-eb5b-4f1a-aa64-9e8f448c33ed&th=1'
  }
  ]);

// const budget = 50000;
// const priceLabel = computed(() => {
//   return budget < item1.price ? 'too expensive...' : item1.price + ' yen';
// });

// const { price } = toRefs(item1);
// watch(price, () => {
//   console.log('item1 changed.');
// });

const buy = (itemName: string) => {
  alert('Are you sure to buy ' + itemName + '?');
}

const input1 = ref<string>('');
const input2 = ref<number>(0);
const input3 = ref<string>('');

const add = () => {
  const newItem: Item = {
    name: input1.value,
    price: input2.value,
    url: input3.value
  }
  items.push(newItem);
}
const clear = () => {
  input1.value = '';
  input2.value = 0;
  input3.value = '';
}

const deleteItem = (index: number) => {
  items.value.splice(index, 1);
}

</script>

<template>
  <div class="container">
    <h1>Payment</h1>
    <table>
      <tr>
        <td>Item Name</td>
        <td><input v-model="input1"></td>
      </tr>
      <tr>
        <td>Price</td>
        <td><input v-model="input2"></td>
      </tr>
      <tr>
        <td>URL</td>
        <td><input v-model="input3"></td>
      </tr>
    </table>
    <div>
      <button @click="add">Add</button>
      <button @click="clear">Clear</button>
    </div>
    <div class="payment" v-for="(item, index) in items" :key="item">
      <label>{{ item.name }}</label>
      <label>{{ item.price }}</label>
      <a :href="item.url">bought at...</a>
      <button @click="buy(item.name)">BUY</button>
      <button @click="deleteItem(index)">DELETE</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.payment {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 80px;
  width: 400px;
  background-color: aliceblue;
  margin-top: 8px;
}

button {
  margin-right: 10px;
}

input {
  margin-bottom: 8px;
}

label {
  font-size: 20px;
  font-weight: bold;
}
</style>