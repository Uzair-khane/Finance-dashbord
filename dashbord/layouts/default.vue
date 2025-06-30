<!-- layouts/default.vue -->
<template>
  <div class="flex items-start">
    <div>
      <SidebarMenu />
    </div>
    <div class="p-10">
      <slot />
    </div>
  </div>
</template>
