<template>
  <div
    ref="screenRef"
    class="bg-indigo-400 w-screen h-screen flex items-center justify-center"
  >
    <div
      ref="canvasRef"
      :class="canvasDependency"
      class="bg-amber-200"
      :style="{
        aspectRatio: RATIO,
      }"
    ></div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";
import { useElementSize } from "@vueuse/core";
import { RATIO } from "@/common/config";

const screenRef = ref();
const canvasRef = ref();
const { width, height } = useElementSize(screenRef);

const canvasDependency = computed(() =>
  width.value / height.value < RATIO ? "w-full" : "h-full"
);
</script>
