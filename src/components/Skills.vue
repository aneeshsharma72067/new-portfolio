<template>
  <section
    class="max-w-full main-item overflow-hidden flex flex-col gap-16 font-bold items-center"
    id="skills"
  >
    <h1 class="sm:text-8xl text-6xl">
      <span class="text-shadow-red">Skill</span> Set
    </h1>
    <div class="flex gap-14 mt-10 mb-3 slide-track">
      <img
        v-for="image in images1"
        :src="getImageUrl(image)"
        :key="image"
        alt="not-found"
        class="h-24 hover:scale-125 duration-500"
      />
    </div>
    <div class="flex gap-14 mb-10 mt-3 slide-track">
      <img
        v-for="image in images2"
        :src="getImageUrl(image)"
        :key="image"
        alt="not-found"
        class="h-24 hover:scale-125 duration-500"
      />
    </div>
  </section>

  <!-- <div
    v-if="loading"
    class="hero h-[70vh] neuromorphism-bg main-item !bg-gradient-to-r !from-zinc-500 !to-red-300 animate-pulse p-0"
  ></div> -->
</template>

<script>
export default {
  name: "SkillsComponent",
  data() {
    return {
      loading: true,
      images1: [
        "html",
        "css",
        "js",
        "php",
        'python',
        'c',
        "tailwind-css",
        "bootstrap",
        "react-native",
        "html",
        "css",
        "js",
        
      ],
      images2:[
        "express-js",
        "mongodb",
        "nodejs",
        "vue-js",
        "nextjs",
        "mysql",
        "figma",
        "npm",
        "firebase",
        "express-js",
        "mongodb",
        "nodejs",
      ]
    };
  },
  mounted() {
    setTimeout(() => {
      this.loading = false;
    }, 1000);
  },
  methods: {
    getImageUrl(imageName) {
      // This path must be correct for your file
      return new URL(
        `../assets/images/icons8-${imageName}-144.png`,
        import.meta.url
      );
    },
  },
};
</script>

<style lang="css" scoped>
.skillsSection-enter-from {
  opacity: 0;
}
.skillsSection-enter-to {
  opacity: 1;
}
.skillsSection-enter-active {
  transition: 0.3s ease-in-out all;
}
.text-shadow-red {
  text-shadow: 0 0 10px #f14343;
  color: var(--primary-dark);
}
.slide-track {
  animation: scroll 20s linear infinite;
  /* transform: translateX(calc((-250px * 9))); */
  /* transform: translateX(120px); */
}

.slide-track:hover {
  animation-play-state: paused;
}

@keyframes scroll {
  0% {
    transform: translateX(120px);
  }
  100% {
    transform: translateX(calc((-250px * 9)));
  }
}

@media only screen and (max-width: 560px) {
  .slide-track {
    gap: 1rem;
  }
}
</style>