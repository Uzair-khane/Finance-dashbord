]<template>
  <div class="h-screen border-slate-200 sm:border-r">
    <!-- Header with logo and hamburger icon -->
    <header class="flex items-center justify-between p-4">
      <div class="flex items-center gap-3">
        <Logo />
        <p class="font-bold text-lg">Nuxt-Finance</p>
      </div>

      <!-- Hamburger icon for mobile (right aligned) -->
      <div class="md:hidden  ">
        <button @click="isMenuOpen = !isMenuOpen" aria-label="Toggle menu">
          <Icon class="ml-36"
            v-if="!isMenuOpen"
            name="heroicons-solid:menu"
            size="35"
            color="black"
          />
        </button>
      </div>
    </header>

    <!-- Sidebar menu for desktop -->
    <div class="hidden md:block px-4">
      <div class="grid gap-4 mt-7">
        <nuxt-link
          v-for="(item, index) in items"
          :key="index"
          :href="item.path"
          class="flex items-center gap-3.5 px-5 py-2 transition cursor-pointer hover:bg-neutral-100"
        >
          <Icon v-if="item.icon" :name="item.icon" size="20" color="black" />
          <span>{{ item.title }}</span>
        </nuxt-link>
      </div>
    </div>

    <!-- Fullscreen Mobile Menu Overlay -->
    <div
      v-if="isMenuOpen"
      class="fixed inset-0 bg-white z-50 flex flex-col pt-16"
    >
      <!-- ❌ Close Button at Top Right -->
      <div class="absolute top-4 right-4">
        <button @click="isMenuOpen = false" aria-label="Close menu">
          <Icon name="heroicons-solid:x" size="35" color="black" />
        </button>
      </div>

      <!-- Menu Items -->
      <div class="flex flex-col px-6 mt-8">
        <nuxt-link
          v-for="(item, index) in items"
          :key="index"
          :href="item.path"
          class="flex items-center gap-3.5 px-4 py-4 text-xl border-b border-gray-200"
          @click="isMenuOpen = false"
        >
          <Icon v-if="item.icon" :name="item.icon" size="24" color="black" />
          <span>{{ item.title }}</span>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const items = ref([
  { title: "Overview", path: "/", icon: "heroicons-solid:collection" },
  { title: "Transactions", path: "/transaction", icon: "heroicons-solid:arrows-right-left" },
  { title: "Account", path: "/account", icon: "heroicons-solid:user-circle" },
  { title: "Contacts", path: "/contacts", icon: "heroicons-solid:users" },
  { title: "Settings", path: "/settings", icon: "heroicons-solid:cog-6-tooth" },
])

const isMenuOpen = ref(false)
</script>
