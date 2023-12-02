<template>
  <div class="container">
    <NavbarVue />
    <MainComponent />
    <SocialMedia />
  </div>
</template>

<script>
import MainComponent from "./components/Main.vue";
import NavbarVue from "./components/Navbar.vue";
import SocialMedia from "./components/SocialMedia.vue";
export default {
  name: "App",
  components: {
    NavbarVue,
    MainComponent,
    SocialMedia,
  },
  data() {
    return {
      current:
        window.location.hash.slice(1) === ""
          ? "home"
          : window.location.hash.slice(1),
    };
  },
  mounted() {
    document.addEventListener("DOMContentLoaded", () => {
      const sections = document.querySelectorAll("section[id]");
      console.log(sections);
      // Add an event listener listening for scroll
      window.addEventListener("scroll", navHighlighter);

      function navHighlighter() {
        // Get current scroll position
        let scrollY = window.scrollY;

        // Now we loop through sections to get height, top and ID values for each
        sections.forEach((current) => {
          const sectionHeight = current.offsetHeight;
          const sectionTop = current.offsetTop - 50;
          const sectionId = current.getAttribute("id");
          if (scrollY > sectionTop && scrollY <= sectionTop + sectionHeight) {
            console.log(sectionId);
            document
              .querySelector(`a[href='#${sectionId}']`)
              .parentElement.classList.add("nav-active");
          } else {
            document
              .querySelector(`a[href='#${sectionId}']`)
              .parentElement.classList.remove("nav-active");
          }
        });
      }
    });
  },
};
</script>

<style>
#app {
  font-family: "MonoSans";
  background: #1c1c1c;
  color: white;
}

.container {
  width: 95vw;
  display: flex;
  gap: 1rem;
  margin: 0 auto;
}
@media only screen and (max-width: 560px) {
  #app {
    background: #3d3d3d;
  }
  .container {
    width: 100vw;
    display: block;
    overflow-x: hidden;
  }
}

@media only screen and (max-width: 1600px) {
  .container {
    max-width: 100vw;
  }
}
</style>
