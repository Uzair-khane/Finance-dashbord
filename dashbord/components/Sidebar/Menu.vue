<template>
  <header
    class="flex items-center gap-3 p-4 hover:scale-[101%] transition cursor-pointer"
  >
    <Logo />
    <p class="font-bold">Nuxt-Finance</p>
  </header>

  <div class="px-4 grow">
    <div class="grid gap-4">
      <div
        v-for="(item, index) in items"
        :key="index"
        class="flex items-center gap-3.5 px-5 py-1 transition cursor-pointer hover:bg-neutral-100"
      >
        <!-- Show icon only if defined -->
        <Icon v-if="item.icon" :name="item.icon" size="20" color="black" />
        <span>{{ item.title }}</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const items = ref([
  {
    title: "Overview",
    path: "/overview",
    icon: "heroicons-solid:collection"
  },
  {
    title: "Transactions",
    path: "/transactions",
    icon: "heroicons-solid:arrows-right-left"
  },
  {
    title: "Account",
    path: "/account",
    icon: "heroicons-solid:user-circle"
  },
  {
    title: "Contacts",
    path: "/contacts",
    icon: "heroicons-solid:users"
  },
  {
    title: "Settings",
    path: "/settings",
    icon: "heroicons-solid:cog-6-tooth"
  },
])
</script>
