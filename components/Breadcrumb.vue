<template>
  <div class="flex text-sm text-[#333] items-center overflow-x-auto px-4 -ml-4 w-[calc(100%+2rem)]">
    <span v-for="(link, i) in format" :key="link.name" class="flex items-center">
      <NuxtLink v-if="link.slug" :to="link.slug" class="hover:text-primary hover:underline">{{ link.name }}</NuxtLink>
      <span v-else class="font-semibold whitespace-nowrap">{{ link.name }}</span>
      <span v-if="i + 1 < format.length" class="mx-3 w-1.25 relative top-0.25">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="63.925 63.925 224.1 384.1">
          <path d="M278.6 233.4c12.5 12.5 12.5 32.8 0 45.3l-160 160c-12.5 12.5-32.8 12.5-45.3 0s-12.5-32.8 0-45.3L210.7 256 73.4 118.6c-12.5-12.5-12.5-32.8 0-45.3s32.8-12.5 45.3 0l160 160z" fill="#7f54b2"/>
        </svg>
      </span>
    </span>
  </div>
</template>

<script>
export default {
  props: {
    format: { type: Array, default: [] },
  },
};
</script>
<style lang="scss">
.overflow-x-auto::-webkit-scrollbar {
  display: none;
}
</style>