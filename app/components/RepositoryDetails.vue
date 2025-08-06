<template>
  <div>
    <h3 class="text-center text-xl">{{ repositoryData?.name }}</h3>
    <div class="flex flex-col gap-2 text-primary-50/90 mt-2">
      <div class="text-primary-50/70 text-sm text-center">{{ repositoryData?.description }}</div>
      <div class="flex items-center justify-between">
        <p class="flex items-center gap-1">
          <Icon name="lucide:star" />
          Stars
        </p>
        <p>{{ repositoryData?.stargazers_count }}</p>
      </div>

      <div class="flex items-center justify-between">
        <p class="flex items-center gap-1">
          <Icon name="lucide:git-fork" />
          Forks
        </p>
        <p>{{ repositoryData?.forks_count }}</p>
      </div>

      <div class="flex items-center justify-between">
        <p class="flex items-center gap-1">
          <Icon name="lucide:bug" />
          Open Issues
        </p>
        <p>{{ repositoryData?.open_issues_count }}</p>
      </div>
    </div>

    <div class="flex justify-center my-4">
      <UButton
        color="secondary"
        icon="i-lucide-rotate-ccw"
        size="lg"
        label="Refresh"
        @click="handleSearch"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
  import type {
    GithubRepositoryResponse,
    Item,
  } from '~/interfaces/github-repository-response.interface';

  import type { FetchError } from 'ofetch';

  const toast = useToast();
  const page = Math.floor(Math.random() * 10) + 1;
  const loadingStatus = useState('status');
  const repositoryDataList = useState<GithubRepositoryResponse | undefined>('dataList');
  const repositoryData = useState<Item | undefined>('data');
  const unexpectedError = useState<FetchError<unknown> | undefined>('error');
  const queryValue = useState<string>('query');

  async function handleSearch() {
    toast.add({
      title: `Searching a repository for ${queryValue.value}`,
      color: 'secondary',
    });
    const { data, status, error } = await useFetch<GithubRepositoryResponse>(
      `https://api.github.com/search/repositories?q=${queryValue.value}&page=${page}`,
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
  }
</script>
