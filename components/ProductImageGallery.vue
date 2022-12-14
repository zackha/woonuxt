<template>
  <div class="relative pointer-events-auto">
    <div class="flex h-full items-center border-b border-[#e6e6e6] overflow-auto md:(border rounded-[1.25rem] w-[400px]) lg:w-[500px]">
      <NuxtImg class="w-full object-center" width="1000px" format="webp" fit="outside" :src="firstImage" v-show="imageToShow === null" />
      <NuxtImg class="w-full object-center" width="1000px" format="webp" fit="outside" :src="mainImage" v-show="imageToShow === 0" />
      <NuxtImg class="w-full object-center" width="1000px" format="webp" fit="outside" v-for="(node, i) in gallery.nodes" :key="i" :src="node.sourceUrl" v-show="imageToShow === i + 1"/>
    </div>

    <div class="bullets-wrapper">
      <div v-if="gallery.nodes.length" class="bullets-container gap-2">
        <NuxtImg :class="{focused: imageToShow === null || imageToShow === 0}" class="opacity-60 w-5 rounded-sm sm:w-10 md:w-6 lg:w-8" width="200px" format="webp" fit="outside" :src="firstImage" @mouseover="changeImage(null)" />
        <NuxtImg :class="{focused: imageToShow === i + 1}" class="opacity-60 w-5 rounded-sm sm:w-10 md:w-6 lg:w-8" width="200px" format="webp" fit="outside" v-for="(node, i) in gallery.nodes" :key="i" :src="node.sourceUrl" @mouseover="changeImage(i + 1)"/>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      imageToShow: 0,
    };
  },
  props: ["firstImage", "mainImage", "gallery", "node"],
  methods: {
    changeImage(index) {
      this.imageToShow = index;
    },
  },
  watch: {
    mainImage(newImage) {
      this.imageToShow = 0;
    },
  },
};
</script>
<style lang="scss">
.focused {
  opacity: 1;
}
.bullets-wrapper {
  padding: 0.5rem;
  background-color: hsla(0, 0%, 100%, 0.7);
  border-radius: 0.875rem;
  position: absolute;
  left: 50%;
  bottom: 0.563rem;
  transform: translate(-50%);
}
.bullets-wrapper .bullets-container {
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  border-radius: 0.5rem;
}
</style>
