<template>
  <v-container
    ><v-row
      ><v-col cols="12" lg="4" class="my-4 flex gap-5 align-center ml-10"
        ><h1
          class="text-3xl mt-4 text-sky-700 mb-6 text-center"
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
          style="border: 2px solid greenyellow"
          class="rounded-full move-up-down"
          src="/src/imgs/me.jpg"
          alt="" /></v-col
      ><v-col cols="12" lg="1" class="text-center flex"
        ><div
          class="social-icons flex justify-center text-center mx-auto gap-5 align-center my-auto"
        >
          <a href="https://www.facebook.com/Mostafazayed2020" target="_blank"
            ><v-icon>mdi-facebook</v-icon></a
          >
          <a href="https://wh.ms/201099658770" target="_blank">
            <v-icon>mdi-whatsapp</v-icon>
          </a>
        </div></v-col
      ></v-row
    >
  </v-container>
</template>

<script setup>
import Typed from "typed.js";
import { onMounted, onBeforeUnmount } from "vue";

const options = {
  strings: ["Mostafa Zayed", "a web developer"],
  typeSpeed: 100,
  backSpeed: 20,
  loop: true,
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
