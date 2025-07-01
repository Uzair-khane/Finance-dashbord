<!-- layouts/default.vue -->
<template>
  <div class="grid grid-cols-5">
    <div class="col-span-1">
      <SidebarMenu />
    </div>
    <div class="p-10 col-span-4">
      <slot />
    </div>
  </div>
</template>
