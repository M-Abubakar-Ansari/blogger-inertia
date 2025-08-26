<script setup lang="ts">
import type { HTMLAttributes } from "vue";
import AppLogo from "./AppLogo.vue";
import AppIcon from "./AppIcon.vue";

defineOptions({
  inheritAttrs: false,
});

interface Props {
  className?: HTMLAttributes["class"];
}

defineProps<Props>();
</script>

<template>
    <div class="flex">
        <AppIcon />
        <AppLogo />
    </div>
</template>
