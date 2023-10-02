<template>
  <div class="main">
    <HeroComponent />
    <AboutComponent />
    <SkillsComponent />
    <ProjectsComponent />
    <ContactComponent />
  </div>
</template>

<script>
import HeroComponent from "./Hero.vue";
import AboutComponent from "./About.vue";
import ProjectsComponent from "./Projects.vue";
import SkillsComponent from "./Skills.vue";
import ContactComponent from "./Contact.vue";
export default {
  name: "MainComponent",
  components: {
    HeroComponent,
    AboutComponent,
    ProjectsComponent,
    SkillsComponent,
    ContactComponent,
  },
};
</script>

<style lang="css" scoped>
.main {
  flex-grow: 20;
  background: #1c1c1c;
  min-height: 100vh;
  display: flex;
  gap: 3rem;
  flex-direction: column;
  padding: 3rem;
}

@media only screen and (max-width: 560px) {
  .main {
    background: #3d3d3d;
    padding: 10px;
  }
}
</style>