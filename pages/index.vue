<template>
  <section class="flex items-center w-full">
    <div class="flex items-center px-20 py-5 w-full justify-around" v-if="!hidden">
      <!-- <p class="text-3xl font-bold underline font-[Poppins]">
        Type Anything
      </p> -->
      <UInput
        v-model="value"
        size="xl"
        input-class="text-3xl"
        placeholder="Type something..."
        variant="none"
        autofocus
      />
      <URange v-model="font_size" :min="0" :max="100" class="w-64" />
      <UCheckbox v-model="selected" name="notifications" label="Animation" />
    </div>
    <UButton
    icon="line-md:watch-loop"
    size="sm"
    color="primary"
    square
    variant="solid"
    @click="hidden = !hidden"
    @mouseover="hover = true"
    @mouseleave="hover = false"
    :class="['absolute top-5 right-5', { 'hide': hidden && !hover }]"
  />
  </section>
  <section class="flex items-center justify-center min-h-screen">
    <p class="text-wrap text-center" :style="{ fontSize: `${font_size}rem` }" v-if="!selected">
      {{ value }}
    </p>
    <p
      class="text-wrap text-center"
      :style="{ fontSize: `${font_size}rem` }"
      ref="typedElement"
    ></p>
  </section>
</template>


<!-- //--------------------------------------------------Script -->

<script lang="ts" setup>
import Typed from "typed.js";

const typedElement = ref(null);
let typed: any = null;

const value = ref("");
const font_size = ref(10);
const selected = ref(false);
const hidden = ref(false);
const hover = ref(false);

onMounted(() => {
  initTyped();
});

onUnmounted(() => {
  if (typed) {
    typed.destroy();
  }
});

watch(
  () => value.value + selected.value,
  () => {
    initTyped();
  }
);

const initTyped = () => {
  if (typed) {
    typed.destroy();
  }
  const options = {
    strings: [value.value],
    typeSpeed: 100,
    backSpeed: 70,
    loop: true,
    showCursor: false,
  };

  if (selected.value) {
    typed = new Typed(typedElement.value, options);
  } else {
    return;
  }
};
</script>
<!-- //-----------------------------------------------------------------Style -- -->
<style>
.hide {
  opacity: 0;
  transition: opacity 0.3s;
}
</style>
