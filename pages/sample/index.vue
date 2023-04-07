<script setup lang="ts">
type Menu = {
  name: string
  to: string
  active: boolean
}
const menus: Menu[]= [
  {
    name: 'TODO List',
    to: '/sample/todo',
    active: true
  },
  {
    name: '準備中...',
    to: '/',
    active: false
  }
];
</script>

<template>
  <Header title="Sample Page"/>
  <ul v-for="menu in menus">
    <li><NuxtLink :to="menu.to" :class="{ 'disabled' : !menu.active }">{{ menu.name }}</NuxtLink></li>
  </ul>
  <Footer />
</template>

<style scoped>
.disabled {
  pointer-events: none;
  text-decoration: none;
}

</style>