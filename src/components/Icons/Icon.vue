<template>
  <li class="nav-icon" :class="active ? 'nav-active' : ''">
    <a :href="link">
      <svg
        class="duration-300"
        :width="size"
        :height="size"
        fill="#ffffff"
        viewBox="0 0 24 24"
        xmlns="http://www.w3.org/2000/svg"
      >
        <slot></slot>
      </svg>
    </a>
  </li>
</template>

<script>
export default {
  name: "HomeIcon",
  data() {
    return {
      size: 30,
    };
  },
  props: {
    active: Boolean,
    link: String,
  },
  inject: ["current"],
};
</script>

<style lang="css" scoped>
.nav-icon {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: 0.3s;
  z-index: 2;
  border-radius: 10px 0 0 10px;
  position: relative;
  overflow: hidden;
  border: 2px solid transparent;
}

.nav-icon > a {
  padding: 5px;
  width: inherit;
  height: inherit;
  display: flex;
  align-items: center;
  justify-content: center;
}

.nav-icon:hover {
  margin-left: 20%;
  width: 80%;
}

.nav-icon::before {
  position: absolute;
  content: "";
  width: 100%;
  height: 100%;
  top: 0;
  left: 100%;
  transition: 0.3s ease-in-out;
  z-index: -1;
  border-radius: inherit;
  border: 2px solid var(--primary-red);
  background: var(--primary-red);
}

.nav-active {
  margin-left: 20%;
  width: 80%;
}

.nav-active::before {
  left: 10%;
}
@media only screen and (max-width: 560px) {
  .nav-active::before {
    display: none;
  }

  .nav-icon {
    border-radius: 0;
    border: none;
  }

  .nav-icon > a {
    padding: 5px;
    width: inherit;
    height: inherit;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .nav-icon:hover {
    margin-left: 0;
    width: 100%;
  }

  .nav-icon::before {
    position: absolute;
    content: "";
    width: 100%;
    height: 100%;
    top: 0;
    left: 100%;
    transition: 0.3s ease-in-out;
    z-index: -1;
    border-radius: inherit;
    border: 2px solid var(--primary-red);
    background: var(--primary-red);
  }

  .nav-active {
    margin-left: 0;
    width: 100%;
  }

  .nav-active::before {
    left: 10%;
  }

  .nav-active > a > svg {
    fill: #785cdd;
  }
}
</style>