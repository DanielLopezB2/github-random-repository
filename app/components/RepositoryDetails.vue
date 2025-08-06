<template>
  <div>
    <h3 class="text-center text-xl">Repo Name</h3>
    <div class="flex flex-col gap-2 text-primary-50/90 mt-2">
      <div class="text-primary-50/70 text-sm text-center">Description</div>
      <div class="flex items-center justify-between">
        <p class="flex items-center gap-1">
          <Icon name="lucide:star" />
          Stars
        </p>
        <p>1234</p>
      </div>

      <div class="flex items-center justify-between">
        <p class="flex items-center gap-1">
          <Icon name="lucide:git-fork" />
          Forks
        </p>
        <p>1234</p>
      </div>

      <div class="flex items-center justify-between">
        <p class="flex items-center gap-1">
          <Icon name="lucide:bug" />
          Open Issues
        </p>
        <p>1234</p>
      </div>
    </div>

    <div class="flex justify-center my-4">
      <UButton color="secondary" icon="i-lucide-rotate-ccw" size="lg" label="Refresh" />
    </div>
  </div>
</template>

<script setup lang="ts"></script>
