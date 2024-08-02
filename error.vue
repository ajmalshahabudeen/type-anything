<script setup lang="ts">
import type { NuxtError } from '#app'

const props = defineProps({
  error: Object as () => NuxtError
})
</script>

<template>
  <div class="min-h-screen flex flex-col gap-3 justify-center items-center">
    <h1 class="text-3xl font-[Poppins] font-bold text-red-500">{{ (error as NuxtError).statusCode }}</h1>
    <p class="font-[Poppins] italic inline-flex items-center gap-2">
        <span class="text-3xl">{</span>Bruh where, what are you looking for? <span class="text-3xl">}</span>
    </p>
    <NuxtLink to="/">
        <UButton variant="soft" label="Go back home" />
    </NuxtLink>
  </div>
</template>
