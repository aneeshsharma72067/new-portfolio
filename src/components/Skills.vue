<template>
  <section class="max-w-full main-item flex-wrap flex flex-col gap-16 font-bold items-center" id="skills">
    <h1 class="sm:text-8xl text-6xl">
      <span class="text-shadow-red">Skill</span> Set
    </h1>
    <div class="flex flex-col gap-2 flex-wrap items-center justify-center">
      <div class="flex gap-16 mx-auto w-max -mb-10">
        <div :title="abbrConfig(image)" v-for="image in images1"
          class="bg-gradient-to-br from-slate-500 to-slate-100 p-2 hover:scale-125 duration-300 cursor-pointer hex-bg flex items-center justify-center">
          <img :src="getImageUrl(image)" :key="image" alt="not-found"
            class="h-[4.5rem] place-self-center   duration-500" />
        </div>
      </div>
      <div class="flex gap-16 mx-auto w-max -mb-10">
        <abbr :title="abbrConfig(image)" v-for="image in images2"
          class="bg-gradient-to-br from-slate-500 to-slate-100 p-2 hover:scale-125 duration-300 cursor-pointer hex-bg flex items-center justify-center">
          <img :src="getImageUrl(image)" :key="image" alt="not-found"
            class="h-[4.5rem] place-self-center   duration-500" />
        </abbr>
      </div>
      <div class="flex gap-16 mx-auto w-max -mb-10">
        <abbr :title="abbrConfig(image)" v-for="image in images3"
          class="bg-gradient-to-br from-slate-500 to-slate-100 p-2 hover:scale-125 duration-300 cursor-pointer hex-bg flex items-center justify-center">
          <img :src="getImageUrl(image)" :key="image" alt="not-found"
            class="h-[4.5rem] place-self-center   duration-500" />
        </abbr>
      </div>
      <div class="flex gap-16 mx-auto w-max">
        <abbr :title="abbrConfig(image)" v-for="image in images4"
          class="bg-gradient-to-br from-slate-500 to-slate-100 p-2 hover:scale-125 duration-300 cursor-pointer hex-bg flex items-center justify-center">
          <img :src="getImageUrl(image)" :key="image" alt="not-found"
            class="h-[4.5rem] place-self-center   duration-500 " />
        </abbr>
      </div>
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
        "svelte",
        'python',
        "tailwind-css",

      ],
      images2: [
        "flask",
        "react",
        "typescript",
        "java",
        'c'
      ],
      images3: [
        "express-js",
        "mongodb",
        "nodejs",
        "vuejs",
        "nextjs",
        "mysql",

      ],
      images4: [
        "npm",
        "firebase",
        "spring-boot",
        "figma",
        "postgresql"
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
    abbrConfig(text) {
      if (text === "c") {
        return "C++"
      }
      if (text.length <= 4) {
        return text.toUpperCase();
      }
      if (text.includes('-')) {
        text = text.split('-')
        let part1 = text[0]
        let part2 = text[1]

        if (part1.length <= 3) {
          part1 = part1.toUpperCase();
        }
        else {
          part1 = part1.charAt(0).toUpperCase() + part1.slice(1);
        }
        if (part2.length <= 3) {
          part2 = part2.toUpperCase();
        }
        else {
          part2 = part2.charAt(0).toUpperCase() + part2.slice(1);
        }
        return part1 + " " + part2
      }
      return text.charAt(0).toUpperCase() + text.slice(1)
    }
  },
};
</script>

<style lang="css" scoped>
.hex-bg {
  clip-path: polygon(30% 0%, 70% 0%, 100% 50%, 70% 100%, 30% 100%, 0% 50%);
  width: 6rem;
}

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