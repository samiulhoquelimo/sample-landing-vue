<template>
  <main class="navbar">
    <section class="navbar-brand">
      <img src="/bike_yellow.png" width="45" alt="_"/>
      <h1 class="text-gray-50 text-xl font-semibold lg:text-3xl">Suzuki GSX-R150</h1>
      <button @click="showMenu = true" class="active:scale-95 duration-300 md:hidden" type="button">
        <i class="fa fa-bars text-gray-50 text-2xl"></i>
      </button>
    </section>

    <section :class="showMenu ? 'right-0' : '-right-full'" class="navbar-menu">
      <ul class="navbar-list">
        <span @click="showMenu = false" class=" md:hidden"><i class="fa fa-times text-gray-50"></i></span>
        <template v-for="(menu, x) in menuNavList" :key="x">
          <li :class="menuActive === menu.name ? 'border-b-4 border-blue-400' : ''"
              class="text-gray-50 font-medium duration-300">
            <a @click="menuActive = menu.name" :href="menu.to">{{ menu.name }}</a>
          </li>
        </template>
      </ul>
    </section>
  </main>
</template>

<style scoped>
.navbar {
  @apply z-20 md:flex md:items-center md:justify-between md:px-6 md:py-8 lg:px-10 w-full bg-gradient-to-r from-sky-500 to-indigo-600 fixed top-0 left-0 right-0 px-5 lg:py-8 py-3;
}

.navbar-brand {
  @apply flex items-center justify-between md:gap-3;
}

.navbar-menu {
  @apply duration-300 fixed md:relative top-0 bottom-0 bg-blue-600 md:bg-opacity-0 px-5 lg:px-0 pt-12 md:pt-0;
}

.navbar-list {
  @apply flex flex-col md:flex-row gap-3 md:gap-6 lg:gap-10 lg:text-xl;
}
</style>

<script setup>

import {ref} from 'vue'
import {menuNavList} from "@/data";

const menuActive = ref('Home')
const showMenu = ref(false)
const viewport = ref(window.innerWidth)

if (viewport.value >= 768) showMenu.value = true

</script>
