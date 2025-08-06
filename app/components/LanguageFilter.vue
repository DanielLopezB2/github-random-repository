<template>
  <div class="flex justify-between items-center gap-10 mt-20">
    <USelectMenu v-model="value" :items="items" class="w-[80%]" size="lg" />
    <UButton icon="i-lucide-search" size="lg" label="Find repository" @click="handleSearch" />
  </div>
</template>

<script setup lang="ts">
  import type { FetchError } from 'ofetch';
  import type {
    GithubRepositoryResponse,
    Item,
  } from '~/interfaces/github-repository-response.interface';

  const items = languages;
  const value = ref<string>(languages.value[0] ?? '');
  const page = Math.floor(Math.random() * 10) + 1;
  const loadingStatus = useState('status', () => 'success');
  const repositoryDataList = useState<GithubRepositoryResponse | undefined>(
    'dataList',
    () => undefined,
  );
  const repositoryData = useState<Item | undefined>('data', () => undefined);
  const unexpectedError = useState<FetchError<unknown> | undefined>('error', () => undefined);
  const queryValue = useState<string>('query', () => '');

  async function handleSearch() {
    const { data, status, error } = await useFetch<GithubRepositoryResponse>(
      `https://api.github.com/search/repositories?q=${value.value}&page=${page}`,
    );
    loadingStatus.value = status.value;
    repositoryDataList.value = data.value;
    const items = data.value?.items || [];
    if (items.length > 0) {
      const randomIndex = Math.floor(Math.random() * items.length);
      repositoryData.value = items[randomIndex];
    } else {
      repositoryData.value = undefined;
    }
    unexpectedError.value = error.value;
    queryValue.value = value.value;
  }
</script>
