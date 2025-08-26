<script setup lang="ts">
import type { HTMLAttributes } from "vue";
import AppLogo from "./AppLogo.vue";
import AppIcon from "./AppIcon.vue";
import { Link } from "@inertiajs/vue3";
import { dashboard } from "@/routes";

defineOptions({
  inheritAttrs: false,
});

interface Props {
  icon?: HTMLAttributes["class"];
  logo1?: HTMLAttributes["class"];
  logo2?: HTMLAttributes["class"];
}
const props = defineProps<Props>();
</script>

<template>
  <Link href="/" class="flex cursor-pointer">
    <AppIcon :className="props.icon" />
    <AppLogo :className1="props.logo1" :className2="props.logo2" />
  </Link>
</template>
