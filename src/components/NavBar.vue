<template>
  <div
    class="container grid grid-cols-1 bg-slate-200 h-16 mx-auto shadow-2xl"
    style="position: fixed; z-index: 10"
  >
    <v-container
      ><v-row
        ><v-col class="logo"
          ><h1
            style="cursor: pointer"
            @click="$router.push({ name: 'home' })"
            class="mt-1 text-2xl text-green-500 bg-green-200 w-10 rounded-full text-center"
          >
            M
          </h1></v-col
        ><v-col lg="3" sm="1" v-if="isScreenWide"></v-col
        ><v-col v-if="isScreenWide"
          ><div class="nav-links flex text-center mt-2 gap-20">
            <ul class="flex gap-20">
              <li
                class="hover:translate-y-1 hover:bg-green-200 duration-700"
                style="cursor: pointer; font-weight: bold"
              >
                Home
              </li>
              <li
                class="hover:translate-y-1 hover:bg-green-200 duration-700"
                style="cursor: pointer; font-weight: bold"
              >
                About
              </li>
              <li
                class="hover:translate-y-1 hover:bg-green-200 duration-700"
                style="cursor: pointer; font-weight: bold"
              >
                Services
              </li>
              <li
                class="hover:translate-y-1 hover:bg-green-200 duration-700"
                style="cursor: pointer; font-weight: bold"
              >
                Portfolio
              </li>
            </ul>
            <v-icon class="mr-10 mb-2" @click="toggleMode">{{ icon }}</v-icon>
          </div>
        </v-col>
        <div
          class="small-menu flex gap-16 ml-64"
          style="position: absolute; top: 0; right: 10px"
          v-else
        >
          <v-col
            ><v-icon @click="toggleMode">{{ icon }}</v-icon>
            <v-app-bar-nav-icon @click="openMenu"></v-app-bar-nav-icon
          ></v-col></div></v-row
    ></v-container>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const isScreenWide = ref(false);

const checkScreenWidth = () => {
  isScreenWide.value = window.innerWidth > 1115;
};

onMounted(() => {
  checkScreenWidth();
  window.addEventListener("resize", checkScreenWidth);
});

onBeforeUnmount(() => {
  window.removeEventListener("resize", checkScreenWidth);
});

const isLightMode = ref(true);
const icon = ref("mdi-lightbulb-on");

onMounted(() => {
  const savedMode = localStorage.getItem("themeMode");
  if (savedMode !== null) {
    isLightMode.value = savedMode === "light";
  }
  updateBodyClass();
});

const toggleMode = () => {
  isLightMode.value = !isLightMode.value;
  icon.value = isLightMode.value ? "mdi-lightbulb-on" : "mdi-lightbulb-outline";
  updateBodyClass();

  localStorage.setItem("themeMode", isLightMode.value ? "light" : "dark");
};

const updateBodyClass = () => {
  if (isLightMode.value) {
    document.body.classList.remove("dark-mode");
  } else {
    document.body.classList.add("dark-mode");
  }
};
</script>

<style>
.dark-mode {
  background-color: #333;
  color: #159709;
}
</style>
