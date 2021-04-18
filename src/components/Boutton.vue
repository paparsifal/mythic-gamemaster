<template>
  <div class="p-2 w-full md:w-1/3">
    <button class="px-4 py-2 w-full bg-gray-100 rounded">
      {{ btName }}
    </button>
  </div>
</template>

<script>
export default {
  props: ["btName"],
};
</script>

<style></style>
