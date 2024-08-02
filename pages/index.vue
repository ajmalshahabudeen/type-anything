<template>
  <div class="flex items-center px-20 py-5 justify-around">
    <!-- <p class="text-3xl font-bold underline font-[Poppins]">
      Type Anything
    </p> -->
    <UInput v-model="value"  size="xl" input-class="text-3xl" placeholder="Type something..." variant="none"/>
    <URange v-model="font_size" :min="0" :max="100"/>
  </div>
  <section class="flex items-center justify-center min-h-screen">
    <p class="text-3xl" :style="{ fontSize: `${font_size}rem` }">
      {{ value }}
    </p>
  </section>
</template>

<script lang="ts" setup>

const value = ref('')
const font_size = ref(10)

</script>

<style>

</style>