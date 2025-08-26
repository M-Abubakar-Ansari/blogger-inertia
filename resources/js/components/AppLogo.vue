<script setup lang="ts">
import AppLogoIcon from "@/components/AppLogoIcon.vue";
import AppIcon from "./AppIcon.vue";
import { HTMLAttributes } from "vue";
import { cn } from "@/lib/utils";

interface Props {
  className1?: HTMLAttributes["class"];
  className2?: HTMLAttributes["class"];
}
const props = defineProps<Props>();

</script>

<template>
  <span :class="cn('text-2xl font-bold tracking-tight text-gray-900 dark:text-white ml-2', 
                  props.className1)">
    Blo<span :class="cn('text-red-500', props.className2)">ghoost</span>
  </span>
</template>
