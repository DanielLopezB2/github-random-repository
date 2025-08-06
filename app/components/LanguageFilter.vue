<template>
  <div class="flex justify-between items-center gap-10 mt-20">
    <USelectMenu v-model="value" :items="items" class="w-[80%]" size="lg" />
    <UButton icon="i-lucide-search" size="lg" label="Find repository" />
  </div>
</template>

<script setup lang="ts">
  const items = languages;
  const value = ref<string>(languages.value[0] ?? '');
</script>
