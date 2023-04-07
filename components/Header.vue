<script setup lang="ts">
interface Props {
  title: string
}

const props = withDefaults(defineProps<Props>(), {
  title: ''
});
</script>

<template>
  <div>
    <h1>{{ title }}</h1>
  </div>
</template>