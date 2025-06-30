<template>
  <div class="h-screen sm:border-r-1 border-slate-200">
    <!-- Header with logo and hamburger icon -->
    <header
      class="flex items-center justify-between p-4 hover:scale-[101%] transition cursor-pointer"
    >
      <div class="flex items-center gap-3">
        <Logo />
        <p class="font-bold text-lg">Nuxt-Finance</p>
      </div>
      
      <!-- Hamburger icon for mobile -->
      <div class="md:hidden w-[40px] ml-9">
        <button @click="isMenuOpen = !isMenuOpen" aria-label="Toggle menu">
          <Icon
            v-if="!isMenuOpen"
            name="heroicons-solid:menu"
            size="35"
            color="black"
          />
          <Icon
            v-else
            name="heroicons-solid:x"
            size="35"
            color="black"
          />
        </button>
      </div>
    </header>

    <!-- Navigation menu -->
    <div
      :class="[
        'px-4 transition-all duration-300',
        isMenuOpen ? 'max-h-screen opacity-100' : 'max-h-0 opacity-0 overflow-hidden',
        'md:max-h-screen md:opacity-100 md:overflow-visible',
      ]"
    >
      <div class="grid gap-4 mt-7 md:grid-cols-1">
     
        <nuxt-link :href="item.path"    v-for="(item, index) in items"
          :key="index"  class="flex items-center gap-3.5 px-5 py-1 transition cursor-pointer hover:bg-neutral-100">
          <!-- Show icon only if defined -->
          <Icon v-if="item.icon" :name="item.icon" size="20" color="black" />
          <span>{{ item.title }}</span>
          </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script setup>


const items = ref([
  {
    title: "Overview",
    path: "/overview",
    icon: "heroicons-solid:collection"
  },
  {
    title: "Transactions",
    path: "/transaction",
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

const isMenuOpen = ref(false)
</script>

