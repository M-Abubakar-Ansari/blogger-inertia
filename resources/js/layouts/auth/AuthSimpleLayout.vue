<script setup lang="ts">
import AppIcon from "@/components/AppIcon.vue";
import AppLogo from "@/components/AppLogo.vue";
import { dashboard } from "@/routes";
import { Link } from "@inertiajs/vue3";
import { ref, onMounted, onUnmounted } from "vue";

const mouseX = ref(0);
const mouseY = ref(0);
const auraStyle = ref({});

function updateMouse(e: MouseEvent) {
  mouseX.value = e.clientX;
  mouseY.value = e.clientY;
  auraStyle.value = {
    background: `radial-gradient(100px at ${mouseX.value}px ${mouseY.value}px, rgba(255,0,0,0.4), transparent 80%)`,
  };
}

onMounted(() => window.addEventListener("mousemove", updateMouse));
onUnmounted(() => window.removeEventListener("mousemove", updateMouse));

defineProps<{
  title?: string;
  description?: string;
}>();
</script>

<template>
  <div class="relative w-screen h-screen bg-gray-400 dark:bg-gray-900 overflow-hidden">
    <div class="absolute inset-0 z-0">
      <div
        class="absolute inset-0 pointer-events-none transition-all duration-300"
        :style="auraStyle"
      ></div>

      <div class="absolute inset-0 pointer-events-none overflow-hidden">
        <img
          src="@/assets/ghost1.svg"
          class="absolute w-16 h-16 top-10 left-10 opacity-40 ghost-float-slow"
        />
        <img
          src="@/assets/ghost2.svg"
          class="absolute w-20 h-20 bottom-16 left-1/4 opacity-30 ghost-float-fast"
        />
        <img
          src="@/assets/ghost3.svg"
          class="absolute w-24 h-24 top-1/3 right-12 opacity-20 ghost-float-mid"
        />
      </div>
    </div>

    <div
      class="relative z-10 flex flex-col items-center justify-center w-full h-full px-6 py-12"
    >
      <Link href="/">
        <div class="flex flex-row items-center text-center">
          <AppIcon
            class="w-12 h-12 md:w-16 md:h-16 text-red-500 drop-shadow-lg animate-pulse"
          />
          <AppLogo
            class-name1="text-3xl md:text-6xl font-extrabold tracking-wide text-black dark:text-white"
            class-name2="text-3xl md:text-6xl font-extrabold tracking-wide text-red-600 dark:text-red-500"
          />
        </div>
      </Link>

      <div
        class="w-full max-w-md mt-4 border-red-500 bg-[rgba(255,0,0,0.1)] bg-opacity-25 p-6 rounded-xl shadow-xl"
      >
        <slot />
      </div>
    </div>
  </div>
</template>

<style scoped>
@keyframes ghostFloatSlow {
  0% {
    transform: translateY(0) translateX(0) rotate(0deg);
    opacity: 0.3;
  }
  50% {
    transform: translateY(-20px) translateX(10px) rotate(5deg);
    opacity: 0.6;
  }
  100% {
    transform: translateY(0) translateX(0) rotate(0deg);
    opacity: 0.3;
  }
}
@keyframes ghostFloatMid {
  0% {
    transform: translateY(0) translateX(0) rotate(-2deg);
    opacity: 0.2;
  }
  50% {
    transform: translateY(-15px) translateX(-10px) rotate(2deg);
    opacity: 0.5;
  }
  100% {
    transform: translateY(0) translateX(0) rotate(-2deg);
    opacity: 0.2;
  }
}
@keyframes ghostFloatFast {
  0% {
    transform: translateY(0) translateX(0) rotate(0deg);
    opacity: 0.25;
  }
  50% {
    transform: translateY(-30px) translateX(15px) rotate(-5deg);
    opacity: 0.6;
  }
  100% {
    transform: translateY(0) translateX(0) rotate(0deg);
    opacity: 0.25;
  }
}
.ghost-float-slow {
  animation: ghostFloatSlow 8s ease-in-out infinite;
}
.ghost-float-mid {
  animation: ghostFloatMid 6s ease-in-out infinite;
}
.ghost-float-fast {
  animation: ghostFloatFast 4s ease-in-out infinite;
}
</style>
