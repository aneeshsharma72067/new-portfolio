<template>
  <transition name="heroSection">
    <section
      v-if="!loading"
      class="hero neuromorphism-bg main-item py-10"
      id="home"
      ref="homeRef"
    >
      <div class="user-image">
        <img
          src="../assets/images/figma-dynamic-color.png"
          class="hero-display-icons figma-icon"
          alt=""
        />
        <img
          src="../assets/images/js.avif"
          class="hero-display-icons js-icon"
          alt=""
        />
        <img
          src="../assets/images/webdev-icon.avif"
          class="hero-display-icons webdev-icon"
          alt=""
        />
        <div class="image-container overflow-hidden">
          <Suspense>
            <template #default>
              <img src="../assets/images/user.png" alt="user" />
            </template>
            <template #fallback>
              <div
                class="bg-gradient-to-r from-gray-500 to-red-300 w-full h-full animate-pulse"
              ></div>
            </template>
          </Suspense>
        </div>
      </div>
      <div class="user-details">
        <div class="user-name">
          <span> Aneesh </span>
          <span> Sharma </span>
        </div>
        <div class="user-title">Web Developer</div>
        <div class="user-description">
          <span class="text-2xl text-red-500">“</span>
          In a world filled with bits and bytes, I navigate the ever-evolving
          tech landscape like a digital explorer.<span
            class="text-2xl text-red-500"
            >”</span
          >
        </div>
        <div class="btn-to-contact flex gap-5">
          <button>
            <a
              href="#contact"
              @mouseover="iconHover = true"
              @mouseleave="iconHover = false"
            >
              <span>
                <svg
                  width="30"
                  :class="iconHover && 'moveDown'"
                  height="30"
                  fill="none"
                  stroke="#ffffff"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  viewBox="0 0 24 24"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path d="m5.25 12.563 6.75 6.75 6.75-6.75"></path>
                  <path d="M12 18.375V4.687"></path>
                </svg>
                <svg
                  width="30"
                  :class="iconHover && 'moveDown'"
                  height="30"
                  fill="none"
                  stroke="#ffffff"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  viewBox="0 0 24 24"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path d="m5.25 12.563 6.75 6.75 6.75-6.75"></path>
                  <path d="M12 18.375V4.687"></path>
                </svg>
              </span>
              <span>Let's Talk</span>
            </a>
          </button>
          <button
            class="!bg-red-500 !rounded-xl !px-4 !border-none cv-button flex items-center justify-center gap-2"
            @click="downloadPdf"
          >
            <lord-icon
              src="https://cdn.lordicon.com/frjgvxce.json"
              trigger="hover"
              target=".cv-button"
              colors="primary:#ffffff"
              style="width: 30px; height: 30px"
            >
            </lord-icon>
            <span>My CV</span>
          </button>
        </div>
      </div>
    </section>
  </transition>
</template>

<script>
export default {
  name: "HeroComponent",
  data() {
    return {
      imageLoaded: false,
      loading: true,
      iconHover: false,
    };
  },
  mounted() {
    // this.loading = false;
    this.loading = false;
  },
  methods: {
    onImageLoad() {
      this.imageLoaded = true;
    },
    downloadPdf() {
      const link = document.createElement("a");
      link.href = "/pdf/Aneesh_Sharma.pdf";
      link.target = "_blank";
      link.download = "Aneesh_Sharma.pdf";
      link.click();
    },
  },
};
</script>

<style lang="css" scoped>
.heroSection-enter-from {
  opacity: 0;
}
.heroSection-enter-to {
  opacity: 1;
}
.heroSection-enter-active {
  transition: 0.7s ease-in-out all;
}
.user-image-enter-from {
  opacity: 0;
}
.user-image-enter-to {
  opacity: 1;
}
.user-image-enter-active {
  transition: 0.7s ease-in-out all;
}
.hero {
  display: flex;
  gap: 2rem;
  max-height: 80vh;
  max-width: 70vw;
}

.user-image {
  flex: 1;
  max-height: 100%;
  height: 100%;
  width: 40%;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}
.user-details {
  flex: 1;
  max-width: 45%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 0;
  gap: 1rem;
}

.user-name {
  font-size: 3.5rem;
  display: flex;
  flex-direction: column;
  justify-items: center;
  width: 60%;
  font-family: "B612";
  font-weight: bold;
}

.user-name > span:first-child {
  align-self: flex-start;
}

.user-name > span:last-child {
  align-self: flex-end;
}

.user-title {
  font-size: 1.5rem;
  font-weight: 600;
  background: linear-gradient(to bottom, var(--primary-red), white);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.user-description {
  max-width: 100%;
  text-align: center;
  font-size: 0.9rem;
  font-family: "Inter";
  color: var(--primary-gray);
}

.image-container {
  height: 100%;
  width: 80%;

  z-index: 10;
  display: flex;
  align-items: flex-end;
  justify-content: center;
  position: relative;
  overflow-y: hidden;
}
.image-container img {
  width: 70%;
  z-index: 10;
}

.image-container::after {
  position: absolute;
  content: "";
  width: 100vw;
  height: 100vh;
  z-index: 11;
  top: 0;
  left: 0;
  background: linear-gradient(180deg, transparent 20%, var(--primary-dark) 50%);
}

.image-container::before {
  position: absolute;
  content: "";
  width: 90%;
  aspect-ratio: 1/1;
  background: linear-gradient(
    180deg,
    var(--primary-red-light) 10%,
    white 100%,
    var(--primary-dark) 66%
  );
  border-radius: 50%;
  top: 20%;
  left: 5%;
  z-index: -1;
}

.hero-display-icons {
  width: 20%;
  position: absolute;
  top: 0;
}

.webdev-icon {
  left: 0;
}

.js-icon {
  right: 0;
  top: 2rem;
}

.figma-icon {
  top: auto;
  bottom: 0;
  left: 0;
  z-index: 30;
}

.btn-to-contact {
  transition: 0.3s;
  margin-top: 1rem;
}

.btn-to-contact button {
  width: inherit;
  height: inherit;
  border: none;
  background: none;
}

.btn-to-contact button a {
  width: inherit;
  height: 100%;
  border: 3px solid var(--primary-red-light);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  text-decoration: none;
  font-family: "Inter";
  padding: 5px;
  gap: 5px;
  border-radius: 10px;
  font-size: 1rem;
}

.btn-to-contact button a span {
  display: flex;
  align-items: center;
  justify-content: flex-start;
}

.btn-to-contact button a span:first-child {
  background: var(--primary-red-light);
  border-radius: 5px;
  display: flex;
  height: 2rem;
  align-items: center;
  flex-direction: column;
  justify-content: flex-end;
  overflow: hidden;
}

.moveDown {
  animation: moveDown 400ms forwards ease-in-out;
}

.btn-to-contact button a span:first-child svg {
  flex: 0 0 2rem;
}

@keyframes moveDown {
  from {
    transform: translateY(0);
  }
  to {
    transform: translateY(100%);
  }
}

@media only screen and (max-width: 560px) {
  .hero {
    max-width: 90vw;
    margin: 1rem auto;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    max-height: none;
  }
  .user-image {
    width: 100%;
  }
  .image-container {
    width: 100%;
    overflow: hidden;
  }
  .image-container::after {
    height: 70vh;
  }
  .webdev-icon {
    top: -1rem;
    width: 30%;
  }

  .js-icon {
    width: 25%;
    z-index: 14;
  }

  .figma-icon {
    width: 30%;
    left: -2rem;
  }
  .user-name {
    width: 70%;
  }
  .user-name > span:first-child {
    align-self: flex-start;
  }
  .user-name > span:last-child {
    align-self: flex-end;
  }
  .user-details {
    max-width: none;
  }
}
</style>