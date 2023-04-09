<script setup lang="ts">
interface Props {
  linkTo?: string;
  linkPage?: string;
}

const props = withDefaults(defineProps<Props>(), {
  linkTo: '/',
  linkPage: 'Top'
});
</script>

<template>
  <div>
    <hr>
    <NuxtLink :to="linkTo">{{ linkPage }}</NuxtLink>
  </div>
</template>