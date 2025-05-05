<script setup lang="ts">
import { computed } from "vue";
import { handleBackground } from "../layoutHelper";

const props = defineProps({
  image: {
    type: String,
  },
  class: {
    type: String,
  },
});
const style = computed(() => handleBackground(props.image));
</script>

<template>
  <div class="grid grid-cols-2 w-full max-h-full items-start">
    <div class="slidev-layout default image-right" :class="props.class">
      <slot />
    </div>
    <div class="my-14 mr-14 h-full" :style="style" />
  </div>
</template>
