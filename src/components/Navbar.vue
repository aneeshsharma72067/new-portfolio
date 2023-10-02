<template>
  <div class="navbar neuromorphism-bg 2xl:w-1/2">
    <!-- <div class="slider"></div> -->
    <ul>
      <IconVue :active="current === 'home'" link="#home">
        <path
          fill-rule="evenodd"
          d="m11.52 5.872 7.2 7.2v5.048a1.8 1.8 0 0 1-1.8 1.8H6.12a1.8 1.8 0 0 1-1.8-1.8v-5.048l7.2-7.2Zm6-.952v4.2l-2.4-2.4v-1.8a.6.6 0 0 1 .6-.6h1.2a.6.6 0 0 1 .6.6Z"
          clip-rule="evenodd"
        ></path>
        <path
          fill-rule="evenodd"
          d="M10.672 3.72a1.2 1.2 0 0 1 1.697 0l7.976 7.976a.6.6 0 1 1-.85.85L11.52 4.568l-7.975 7.976a.6.6 0 0 1-.85-.85l7.977-7.975Z"
          clip-rule="evenodd"
        ></path>
      </IconVue>
      <IconVue :active="current === 'about'" link="#about">
        <path
          d="M15.592 3.027C14.68 2.042 13.406 1.5 12 1.5c-1.414 0-2.692.54-3.6 1.518-.918.99-1.365 2.334-1.26 3.786C7.348 9.67 9.528 12 12 12c2.472 0 4.648-2.33 4.86-5.195.106-1.439-.344-2.78-1.268-3.778Z"
        ></path>
        <path
          d="M20.25 22.5H3.75a1.454 1.454 0 0 1-1.134-.522 1.655 1.655 0 0 1-.337-1.364c.396-2.195 1.63-4.038 3.571-5.333C7.574 14.132 9.758 13.5 12 13.5c2.242 0 4.426.633 6.15 1.781 1.94 1.294 3.176 3.138 3.571 5.332.091.503-.032 1-.336 1.365a1.453 1.453 0 0 1-1.135.522Z"
        ></path>
      </IconVue>

      <IconVue :active="current === 'skills'" link="#skills">
        <path
          d="m9.75 24-2.455-6.545L.75 15l6.545-2.455L9.75 6l2.455 6.545L18.75 15l-6.545 2.455L9.75 24Z"
        ></path>
        <path
          d="M4.125 8.25 3.02 5.23 0 4.125 3.02 3.02 4.125 0 5.23 3.02l3.02 1.105L5.23 5.23 4.125 8.25Z"
        ></path>
        <path
          d="m18.75 12-1.458-3.792L13.5 6.75l3.792-1.458L18.75 1.5l1.458 3.792L24 6.75l-3.792 1.458L18.75 12Z"
        ></path>
      </IconVue>
      <IconVue :active="current === 'projects'" link="#projects">
        <path
          d="M.75 16.5A2.252 2.252 0 0 0 3 18.75h6.276l-.188 1.5H6.75a.75.75 0 1 0 0 1.5h10.5a.75.75 0 1 0 0-1.5h-2.338l-.188-1.5H21a2.252 2.252 0 0 0 2.25-2.25v-2.25H.75v2.25ZM12 15.75a.75.75 0 1 1 0 1.5.75.75 0 0 1 0-1.5Z"
        ></path>
        <path
          d="M23.25 4.5A2.252 2.252 0 0 0 21 2.25H3A2.252 2.252 0 0 0 .75 4.5v9h22.5v-9Z"
        ></path>
      </IconVue>
      <IconVue :active="current === 'contact'" link="#contact">
        <path
          d="M19.875 3.75H4.125A2.628 2.628 0 0 0 1.5 6.375v11.25a2.628 2.628 0 0 0 2.625 2.625h15.75a2.627 2.627 0 0 0 2.625-2.625V6.375a2.627 2.627 0 0 0-2.625-2.625Zm-.665 4.342-6.75 5.25a.75.75 0 0 1-.92 0l-6.75-5.25a.75.75 0 1 1 .92-1.184L12 11.8l6.29-4.892a.75.75 0 0 1 .92 1.184Z"
        ></path>
      </IconVue>
    </ul>
  </div>
</template>

<script>
import IconVue from "./Icons/Icon.vue";
export default {
  name: "NavbarVue",
  components: {
    IconVue,
  },
  data() {
    return {
      current:
        window.location.hash.slice(1) === ""
          ? "home"
          : window.location.hash.slice(1),
    };
  },
  computed: {
    getCurrent() {
      return this.current;
    },
  },
};
</script>

<style scoped>
.navbar {
  position: sticky;
  top: 17vh;
  background: #1c1c1c;
  color: white;
  height: max-content;
  width: 7vw;
}
ul {
  width: 100%;
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 2rem;
  align-items: center;
  justify-content: space-around;
  margin: 2rem 0;
}
@media only screen and (max-width: 560px) {
  .navbar {
    position: fixed;
    bottom: 1rem;
    top: auto;
    left: 1rem;
    width: max-content;
    padding: 1rem 7px;
    z-index: 20;
    background: rgba(27, 27, 27, 0.3);
    box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
    backdrop-filter: blur(12.5px);
    -webkit-backdrop-filter: blur(12.5px);
    border-radius: 2rem;
    border: 1px solid rgb(78, 51, 233);
  }

  .navbar ul {
    flex-direction: row;
    width: max-content;
    margin-block-start: 0;
    margin-block-end: 0;
    gap: 1.7rem;
    padding: 0 10px;
  }
}
</style>