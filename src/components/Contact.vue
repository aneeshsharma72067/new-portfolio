<template>
  <section
    id="contact"
    class="relative main-item flex flex-col gap-3 mb-12 sm:gap-10 sm:mb-0"
  >
    <transition name="toast">
      <div v-if="toastShow" :class="toastStatus + '-toast'">
        <span class="z-10 relative">{{ toastContent }}</span>
      </div>
    </transition>
    <h1
      class="text-7xl sm:text-right text-center font-bold p-2 sm:px-20 z-10 leading-tight sm:leading-none"
    >
      Get In
      <span class="sm:hidden">&nbsp;&nbsp;&nbsp;&nbsp;</span>
      Touch
    </h1>
    <h1
      class="absolute text-[8rem] sm:text-[10rem] font-extrabold text-[#303030] sm:text-zinc-800 z-0 -top-10 sm:-top-5 left-0"
    >
      CONTACT
    </h1>
    <div
      class="flex items-center sm:items-start justify-center sm:justify-normal flex-wrap sm:gap-10 gap-2"
    >
      <div
        class="flex-1 flex flex-col items-center justify-center sm:items-start mx-auto neuromorphism-bg px-5 py-14 gap-6 sm:my-10 my-2"
      >
        <a href="tel:+917206734591" class="contact-link call-link">
          <lord-icon
            src="https://cdn.lordicon.com/tftaqjwp.json"
            trigger="hover"
            colors="primary:#ffffff"
            target=".call-link"
            style="width: 30px; height: 30px"
          >
          </lord-icon>
          <span>+91 72067 34591</span>
        </a>
        <a
          href="mailto:aneeshsharma1024@gmail.com"
          class="contact-link mail-link"
        >
          <lord-icon
            src="https://cdn.lordicon.com/ehfubvwr.json"
            trigger="hover"
            colors="primary:#ffffff"
            target=".mail-link"
            style="width: 30px; height: 30px"
          >
          </lord-icon>
          <span>aneeshsharma1024@gmail.com</span>
        </a>
        <a
          href="https://api.whatsapp.com/send?phone=7206734591"
          class="contact-link"
        >
          <svg
            width="35"
            height="35"
            fill="#ffffff"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="m2.004 22 1.352-4.968A9.954 9.954 0 0 1 2 12C2 6.477 6.477 2 12 2s10 4.477 10 10-4.477 10-10 10a9.953 9.953 0 0 1-5.03-1.355L2.004 22ZM8.391 7.308a.961.961 0 0 0-.371.1 1.293 1.293 0 0 0-.294.228c-.12.113-.188.211-.261.306A2.729 2.729 0 0 0 6.9 9.62c.002.49.13.967.33 1.413.409.902 1.082 1.857 1.971 2.742.214.213.423.427.648.626a9.448 9.448 0 0 0 3.84 2.046l.569.087c.185.01.37-.004.556-.013a1.99 1.99 0 0 0 .833-.231 4.83 4.83 0 0 0 .383-.22s.043-.028.125-.09c.135-.1.218-.171.33-.288.083-.086.155-.187.21-.302.078-.163.156-.474.188-.733.024-.198.017-.306.014-.373-.004-.107-.093-.218-.19-.265l-.582-.261s-.87-.379-1.401-.621a.498.498 0 0 0-.177-.041.482.482 0 0 0-.378.127v-.002c-.005 0-.072.057-.795.933a.35.35 0 0 1-.368.13 1.418 1.418 0 0 1-.191-.066c-.124-.052-.167-.072-.252-.109l-.005-.002a6.011 6.011 0 0 1-1.57-1c-.126-.11-.243-.23-.363-.346a6.298 6.298 0 0 1-1.02-1.268l-.059-.095a.923.923 0 0 1-.102-.205c-.038-.147.061-.265.061-.265s.243-.266.356-.41a4.38 4.38 0 0 0 .263-.373c.118-.19.155-.385.093-.536-.28-.684-.57-1.365-.868-2.041-.059-.134-.234-.23-.393-.249a4.439 4.439 0 0 0-.162-.016 3.385 3.385 0 0 0-.403.004v.001Z"
            ></path>
          </svg>
          <span>Whatsapp</span>
        </a>
      </div>
      <div class="flex-1 neuromorphism-bg mt-10">
        <form
          class="w-full p-10 flex flex-col gap-6"
          ref="form"
          @submit.prevent="sendMail"
        >
          <input
            type="text"
            class="bg-transparent outline-none border border-red-400 px-3 rounded-lg w-full text-lg py-2"
            placeholder="Your Name"
            name="from_name"
            v-model="formData.name"
          />
          <input
            type="email"
            class="bg-transparent outline-none border border-red-400 px-3 rounded-lg w-full text-lg py-2"
            placeholder="Your Email"
            name="from_email"
            v-model="formData.email"
          />
          <textarea
            class="bg-transparent outline-none border border-red-400 px-3 rounded-lg w-full text-lg py-2"
            name="message"
            id="message"
            cols="30"
            rows="4"
            placeholder="Message"
            v-model="formData.message"
          ></textarea>
          <button
            type="submit"
            :disabled="toastLoading"
            class="border outline-none rounded-md duration-500 w-max border-red-500 hover:bg-red-500 px-4 py-2 text-lg bg-transparent relative flex items-center send-btn justify-center gap-2 disabled:text-slate-400 disabled:hover:bg-transparent"
          >
            <div
              class="w-4/5 h-full py-4 absolute bg-transparent top-0 border-2 border-transparent rounded-md duration-500"
              :class="clicked ? 'clicked' : ''"
              @animationend="clicked = false"
            ></div>
            <span> Send A Message </span>
            <span class="flex items-center justify-center">
              <lord-icon
                src="https://cdn.lordicon.com/pkmkagva.json"
                trigger="hover"
                colors="primary:#ffffff"
                target=".send-btn"
                style="width: 30px; height: 30px"
              >
              </lord-icon
            ></span>
            <div class="lds-ring" v-if="toastLoading">
              <div></div>
              <div></div>
              <div></div>
            </div>
          </button>
        </form>
      </div>
    </div>
  </section>
  <!-- <div
    v-if="loading"
    class="hero h-[70vh] neuromorphism-bg main-item !bg-gradient-to-r !from-zinc-500 !to-red-300 animate-pulse p-0"
  ></div> -->
</template>

<script>
import emailjs from "emailjs-com";
export default {
  name: "ContactComponent",
  data() {
    return {
      loading: true,
      toastContent: "Some thing went wrong !!",
      toastLoading: false,
      toastShow: false,
      toastStatus: "success",
      clicked: false,
      formData: {
        name: "",
        message: "",
        email: "",
      },
    };
  },
  mounted() {
    setTimeout(() => {
      this.loading = false;
    }, 1000);
  },
  methods: {
    setShowToast(status, message = "Some thing went wrong !!") {
      this.toastStatus = status;
      this.toastContent = message;
      this.toastShow = true;
      setTimeout(() => {
        this.toastShow = false;
      }, 4000);
    },
    sendMail() {
      if (this.formData.name.trim() === "") {
        this.setShowToast("error", "Please enter your name !!");
        return;
      }
      if (this.formData.email.trim() === "") {
        this.setShowToast("error", "Please enter your Email !!");
        return;
      }
      if (this.formData.message.trim() === "") {
        this.setShowToast("error", "Please enter a message !!");
        return;
      }
      this.toastLoading = true;
      emailjs
        .send(
          "service_2yacbwr",
          "template_bx0vs8t",
          {
            from_name: this.formData.name,
            from_email: this.formData.email,
            to_name: "Aneesh",
            message: this.formData.message,
          },
          "8w2s-WGbDs1njXNwI"
        )
        .then(() => {
          this.toastLoading = false;
          this.setShowToast("success", "Message sent successfully");
          this.resetForm();
          console.log("success");
        })
        .catch((error) => {
          this.toastLoading = false;
          this.setShowToast("error", "Something Went Wrong");
          console.error("Error sending message:", error);
        });
    },
    resetForm() {
      this.formData.name = "";
      this.formData.email = "";
      this.formData.message = "";
    },
  },
};
</script>

<style lang="css" scoped>
.contactSection-enter-from {
  opacity: 0;
}
.contactSection-enter-to {
  opacity: 1;
}
.contactSection-enter-active {
  transition: 0.3s ease-in-out all;
}
.contact-link {
  @apply flex gap-4 text-lg items-center relative duration-500 hover:text-red-500 w-max;
}

.clicked {
  animation: pulse forwards 0.5s ease-in-out;
}

@keyframes pulse {
  from {
    scale: 1;
    border-color: #ff5b5b;
  }
  to {
    scale: 1.6;
    border-color: transparent;
  }
}

.toast-enter-from {
  transform: translateY(-10rem);
}
.toast-enter-to {
  transform: translateY(0);
}
.toast-enter-active {
  transition: 0.5s ease-in-out all;
}

.toast-leave-from {
  transform: translateY(0);
}
.toast-leave-to {
  transform: translateY(-10rem);
}
.toast-leave-active {
  transition: 0.5s ease-in-out all;
}
.toastBox::before {
  content: "";
  animation: timeOut ease-in-out 4s forwards;
}
@keyframes timeOut {
  from {
    width: 0;
  }
  to {
    width: 100%;
  }
}

.success-toast {
  @apply toastBox fixed top-10 left-[15%] sm:left-[40%] text-xl bg-green-200 py-3 overflow-hidden rounded-lg text-green-600 z-40 before:absolute before:top-0 before:left-0 px-4 text-center before:h-full before:w-0 before:bg-green-300 before:z-0 shadow-[0_0_20px_#20aa53];
}
.error-toast {
  @apply toastBox fixed top-10 left-[15%] sm:left-[40%] text-xl bg-red-200 px-4 py-3 overflow-hidden rounded-lg text-red-600 z-40 before:absolute before:top-0 before:left-0 before:h-full before:w-0 before:bg-red-300 before:z-0 shadow-[0_0_20px_#f72c2c];
}

.lds-ring {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  width: 40px;
  height: 100%;
}
.lds-ring div {
  box-sizing: border-box;
  display: block;
  position: absolute;
  width: 24px;
  height: 24px;
  border: 2px solid #f72c2c;
  border-radius: 50%;
  animation: lds-ring 1.2s cubic-bezier(0.5, 0, 0.5, 1) infinite;
  border-color: #f72c2c transparent transparent transparent;
}
.lds-ring div:nth-child(1) {
  animation-delay: -0.45s;
}
.lds-ring div:nth-child(2) {
  animation-delay: -0.3s;
}
.lds-ring div:nth-child(3) {
  animation-delay: -0.15s;
}
@keyframes lds-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>