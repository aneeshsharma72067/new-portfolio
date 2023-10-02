<template>
  <div
    class="flex-1 h-max flex flex-col gap-3 items-center overflow-hidden rounded-lg bg-neutral-900 border-2 hover:border-red-500 border-transparent duration-500 cursor-pointer"
  >
    <div
      class="project-image w-full h-max max-h-40 overflow-hidden group relative duration-500"
    >
      <img
        :src="getImageUrl()"
        alt="not-found"
        class="group-hover:scale-150 duration-500"
      />
      <div
        class="w-full h-full bg-zinc-800 group-hover:opacity-90 duration-300 opacity-0 z-10 absolute top-0 left-0 p-4"
      >
        <p class="group-hover:translate-x-0 -translate-x-44 duration-500">
          {{ description }}
        </p>
      </div>
    </div>
    <div class="w-full text-center py-4 flex flex-col gap-10">
      <p class="h-8 text-slate-100 text-lg px-2 font-bold">{{ projectName }}</p>
      <div class="flex gap-5 px-3 justify-center items-center">
        <a
          v-if="previewUrl"
          class="flex gap-2 px-3 py-2 items-center justify-center rounded-md bg-zinc-800 hover:bg-blue-500 text-slate-100 duration-300"
          :href="previewUrl"
          target="_blank"
        >
          <span class="flex items-center justify-center"
            ><svg
              width="25"
              height="25"
              fill="#ffffff"
              viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                fill-rule="evenodd"
                d="M12.795 6.375a.625.625 0 0 0-.625-.625H3.875A1.875 1.875 0 0 0 2 7.625v12.5A1.875 1.875 0 0 0 3.875 22h12.5a1.875 1.875 0 0 0 1.875-1.875V11.83a.624.624 0 1 0-1.25 0v8.295a.624.624 0 0 1-.625.625h-12.5a.625.625 0 0 1-.625-.625v-12.5A.625.625 0 0 1 3.875 7h8.295a.625.625 0 0 0 .625-.625Z"
                clip-rule="evenodd"
              ></path>
              <path
                fill-rule="evenodd"
                d="M22 2.625A.625.625 0 0 0 21.375 2h-6.25a.625.625 0 1 0 0 1.25h4.741L9.682 13.432a.626.626 0 1 0 .885.886L20.75 4.134v4.741a.625.625 0 1 0 1.25 0v-6.25Z"
                clip-rule="evenodd"
              ></path></svg
          ></span>
          <span class="flex items-center justify-center">Preview</span>
        </a>
        <a
          class="flex gap-2 px-3 py-2 rounded-md bg-zinc-800 hover:bg-red-500 text-slate-100 duration-300"
          :href="repoUrl"
          target="_blank"
        >
          <span class="flex items-center justify-center"
            ><svg
              width="25"
              height="25"
              fill="#ffffff"
              viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M12 1.5C6.202 1.5 1.5 6.323 1.5 12.267c0 4.758 3.01 8.79 7.181 10.214a.82.82 0 0 0 .178.019c.39 0 .54-.286.54-.534 0-.258-.01-.933-.015-1.833a4.802 4.802 0 0 1-1.059.126c-2.02 0-2.48-1.57-2.48-1.57-.478-1.242-1.167-1.575-1.167-1.575-.914-.642-.005-.66.066-.66h.004c1.055.093 1.608 1.115 1.608 1.115.525.919 1.228 1.176 1.857 1.176a2.953 2.953 0 0 0 1.2-.28c.093-.695.365-1.168.665-1.44-2.33-.272-4.781-1.195-4.781-5.32 0-1.177.408-2.138 1.078-2.888-.108-.272-.469-1.369.103-2.85a.874.874 0 0 1 .235-.023c.38 0 1.237.145 2.653 1.13a9.76 9.76 0 0 1 5.259 0c1.416-.985 2.273-1.13 2.653-1.13a.873.873 0 0 1 .235.023c.571 1.481.21 2.578.103 2.85.67.755 1.078 1.716 1.078 2.888 0 4.134-2.456 5.043-4.796 5.31.375.333.713.99.713 1.993 0 1.439-.014 2.601-.014 2.953 0 .253.145.539.534.539a.9.9 0 0 0 .188-.019c4.176-1.425 7.181-5.46 7.181-10.214C22.5 6.323 17.798 1.5 12 1.5Z"
              ></path></svg
          ></span>
          <span class="flex items-center justify-center">Github</span>
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  imageName: String,
  projectName: String,
  description: String,
  repoUrl: String,
  previewUrl: String,
});
function getImageUrl() {
  // This path must be correct for your file
  return new URL(`../assets/images/${props.imageName}`, import.meta.url);
}
</script>
<style scoped>
</style>