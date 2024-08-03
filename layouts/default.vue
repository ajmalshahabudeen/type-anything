<template>
  <div>
    <SpeedInsights/>
    <slot />
  </div>
</template>

<script lang="ts" setup>
import { SpeedInsights } from "@vercel/speed-insights/nuxt"
</script>

<style>

</style>