<template>
  <div>
    <!-- Header -->
    <div class="flex sm:justify-between justify-center mt-24 gap-6 w-full ">
      <h1 class="font-bold text-[24px] font-sans mr-[120px]">Dashboard</h1>
     
     
    </div>

    <!-- Cards -->
    <div class="sm:flex ml-[-30px] grid flex-wrap justify-center px-7 mx-auto gap-8 w-full mt-7">
      <!-- Weekly Card -->
      <div class="bg-red-500 text-white px-10 py-3 rounded-[6px]">
        <p class="text-[18px] font-semibold">First Cart ID</p>
        <p>{{ cartId }}</p>
        <p>Static Info</p>
      </div>

      <!-- Monthly Card -->
      <div class="bg-green-500 text-white px-10 py-3 rounded-[6px]">
        <p class="text-[18px] font-semibold">User ID</p>
        <p>{{ userId }}</p>
        <p>Static Info</p>
      </div>

      <!-- Yearly Card -->
      <div class="bg-blue-600 text-white px-10 py-3 rounded-[6px]">
        <p class="text-[18px] font-semibold">Total Products</p>
        <p>{{ totalProducts }}</p>
        <p>Static Info</p>
      </div>

      <!-- Daily Card -->
      <div class="bg-orange-400 text-white px-10 py-3 rounded-[6px]">
        <p class="text-[18px] font-semibold">Cart Date</p>
        <p>{{ cartDate }}</p>
        <p>Static Info</p>
      </div>
    </div>
  </div>
  <div  class="sm:flex sm:gap-6 sm:mt-20 grid mt-11 gap-10 ml-[-59px]">
    <div class="flex-1 "><Chart /></div>
    <div class="flex-1">
      <Chart2 />
    </div>
  </div>
</template>

<script setup>
// Reactive values
const cartId = ref("");
const userId = ref("");
const totalProducts = ref(0);
const cartDate = ref("");

async function myfun() {
  try {
    const api = await fetch("https://fakestoreapi.com/carts");
    const response = await api.json();
    const firstCart = response[0];
    cartId.value = firstCart.id;
    userId.value = firstCart.userId;
    totalProducts.value = firstCart.products.length;
    cartDate.value = firstCart.date;
  } catch (err) {
    console.error("API error:", err);
  }
}

onMounted(() => {
  myfun();
});
</script>
