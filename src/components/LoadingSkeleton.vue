<template>
  <div
    v-if="loading"
    class="hero h-[70vh] neuromorphism-bg main-item !bg-gradient-to-r !from-zinc-400 !to-gray-600 animate-pulse p-0"
  ></div>
</template>

<script>
export default {
  name: "LoadingSkeleton",
};
</script>

<style lang="scss" scoped>
</style>