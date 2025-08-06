<template>
  <div class="flex flex-col">
    <main-title />
    <language-filter />
    <repository-results v-if="repositoryDataList?.items" />
    <repository-skeleton v-if="loadingStatus !== 'success'" />
    <repository-not-found v-if="repositoryDataList?.items.length === 0" />
    <unexpected-error v-if="unexpectedError" />
  </div>
</template>

<script setup lang="ts">
  import type { GithubRepositoryResponse } from '~/interfaces/github-repository-response.interface';
  import type { FetchError } from 'ofetch';

  const loadingStatus = useState('status');
  const repositoryDataList = useState<GithubRepositoryResponse | undefined>('dataList');
  const unexpectedError = useState<FetchError<unknown> | undefined>('error');
</script>
