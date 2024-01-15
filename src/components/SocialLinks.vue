<template>
  <v-container
    ><v-row
      ><v-col cols="6" class="my-4 flex gap-5 align-center ml-10"
        ><h1
          class="text-3xl text-sky-700 mb-6 text-center"
          style="font-size: 50px; font-weight: bold"
        >
          I'm
        </h1>
        <div
          class="your-element-selector text-3xl text-green-500 text-center"
          style="font-size: 30px; font-weight: bold"
        ></div> </v-col
      ><v-col cols="12" lg="6"
        ><img
          class="rounded-full move-up-down"
          src="/src/imgs/me.jpg"
          alt="" /></v-col></v-row
  ></v-container>
</template>

<script setup>
import Typed from "typed.js";
import { onMounted, onBeforeUnmount } from "vue";

const options = {
  strings: ["Mostafa Zayed", "a web developer"],
  typeSpeed: 100, // سرعة الكتابة بالمللي ثانية
  backSpeed: 20, // سرعة الرجوع بالمللي ثانية
  loop: true, // تكرار النص
};

let typed;

onMounted(() => {
  typed = new Typed(".your-element-selector", options);
});

onBeforeUnmount(() => {
  typed.destroy();
});
</script>

<style>
@keyframes moveUpDown {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
  100% {
    transform: translateY(0);
  }
}

.move-up-down {
  animation: moveUpDown 3s infinite;
}
</style>
