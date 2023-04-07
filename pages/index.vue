<script setup lang="ts">
// TODO .vueファイルについて全体的に、WebStormで開くと変数名などに赤い波線が付く
// （Visual Studio Codeなら何ともないけれど、書き方が間違ってる？）
type Menu = {
  name: string;
  to: string;
};
const menus: Menu[]= [{
  name: 'Sample Page',
  to: '/sample'
}]
</script>

<template>
  <Header title="Top" />
  <NuxtLink v-for="menu in menus" :to="menu.to">{{ menu.name }}</NuxtLink>
</template>
