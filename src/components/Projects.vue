<template>
  <section id="projects" class="neuromorphism-bg main-item flex flex-col gap-10" ref="projectsRef">
    <h1 class="text-6xl font-bold my-10 leading-snug sm:leading-none">
      Project Gallery
    </h1>
    <div class="big-projects flex flex-col w-full gap-10 sm:grid sm:grid-cols-3 ">
      <ProjectComponent imageName="blog-site.png" projectName="HypePost - A Blog Application"
        description="A dynamic blog platform, built with the MERN stack, facilitating blog creation and sharing for content enthusiasts."
        repoUrl="https://github.com/aneeshsharma72067/eride-website.git" />
      <ProjectComponent imageName="car-site.png" projectName="Eride - A Car Booking Platform"
        description="A user-friendly car booking platform developed with PHP for seamless vehicle reservations and travel planning."
        repoUrl="https://github.com/aneeshsharma72067/Blog-App" />
      <ProjectComponent imageName="weather-site.png" projectName="Weather Wave - A Weather Forecasting Website"
        description="A real-time weather forecasting website, crafted using the Vue.js and OpenWeathermap API, providing accurate weather updates at your fingertips."
        repoUrl="https://github.com/aneeshsharma72067/weather-wave" />
      <ProjectComponent imageName="labour-link.png" projectName="LabourLink - A Job Portal for Labours"
        description="LabourLink is user-friendly platform for laborers to find work, built with React.js, Vite, TailwindCSS and Firebase"
        repoUrl="https://github.com/aneeshsharma72067/labourlink-dupe.git" />

    </div>
    <div class="small-projects">
      <h1 class="text-4xl my-10">Mini Projects</h1>
      <div class="flex w-full gap-10 flex-col sm:flex-row">
        <ProjectComponent imageName="movies-site.png" projectName="MovieScraper"
          description="A web scraping application made using OMDB API for searching movies"
          repoUrl="https://github.com/aneesh1024/movies-scraper/"
          previewUrl="https://aneesh1024.github.io/movies-scraper" />
        <ProjectComponent imageName="explorer-site.png" projectName="Github Explorer"
          description="An application using the GitHub API for searching github profiles through their usernames "
          repoUrl="https://github.com/aneesh1024/github-explorer/"
          previewUrl="https://aneesh1024.github.io/github-explorer" />
        <ProjectComponent imageName="random-site.png" projectName="Random User Generator"
          description="A small Vue.js application used to generate random user data using the randomuser API"
          repoUrl="https://github.com/aneeshsharma72067/Random-User-Generator/"
          previewUrl="https://aneeshsharma72067.github.io/Random-User-Generator/" />
      </div>
    </div>
  </section>
  <!-- <LoadingSkeleton v-if="loading" /> -->
  <!-- <div
    v-if="loading"
    class="hero h-[70vh] neuromorphism-bg main-item !bg-gradient-to-r !from-zinc-500 !to-red-300 animate-pulse p-0"
  ></div> -->
</template>

<script>
import ProjectComponent from "./Project.vue";
export default {
  name: "ProjectsComponent",
  components: {
    ProjectComponent,
  },
  data() {
    return {
      loading: true,
      imageUrl: "../assets/images/blog-site.png",
    };
  },
  mounted() {
    setTimeout(() => {
      this.loading = false;
    }, 1000);
  },
  methods: {},
};
</script>

<style lang="css" scoped>
.projectsSection-enter-from {
  opacity: 0;
}

.projectsSection-enter-to {
  opacity: 1;
}

.projectsSection-enter-active {
  transition: 0.2s ease-in-out all;
}

.main-item {
  padding: 2rem;
}
</style>