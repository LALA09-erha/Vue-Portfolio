<script setup>
import { ref, onMounted } from "vue";
import axios from "axios";

const idComponent = ref("contact");
let isLoading = ref(false);
let name = ref("");
let email = ref("");
let subject = ref("");
let message = ref("");

const sosmeds = [
  {
    name: "LinkedIn",
    url: "https://www.linkedin.com/in/fikriainunnajib/",
    icon: "https://cdn-icons-png.flaticon.com/512/174/174857.png",
  },
  {
    name: "GitHub",
    url: "https://github.com/LALA09-erha/",
    icon: "https://cdn-icons-png.flaticon.com/512/25/25231.png",
  },

  {
    name: "Instagram",
    url: "https://www.instagram.com/fikri_erha/",
    icon: "https://cdn-icons-png.flaticon.com/512/1384/1384063.png",
  },
  {
    name: "Blog",
    url: "https://kangtunjuk.blogspot.com/",
    icon: "https://cdn-icons-png.flaticon.com/512/4494/4494538.png",
  },
];

function sendEmail() {
  isLoading.value = true;
  axios
    .post("https://express-rest-api-test.vercel.app/send-email", {
      name: name.value,
      email: email.value,
      subject: subject.value,
      message: message.value,
    })
    .then(() => {
      name.value = "";
      email.value = "";
      subject.value = "";
      message.value = "";
      isLoading.value = false;
      alert("Email sent successfully");
    })
    .catch((error) => {
      isLoading.value = false;
      console.error(error);
      alert("Failed to send email");
    });
}

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries, observer) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("animate-visible");
          observer.unobserve(entry.target);
        }
      });
    },
    { threshold: 0.3 }
  );

  document
    .querySelectorAll(".animate-hidden")
    .forEach((el) => observer.observe(el));
});
</script>

<template>
  <div class="container mx-auto p-6" :id="idComponent">
    <h2
      class="text-3xl font-bold text-gray-900 animate-hidden hover:text-white transition duration-300"
      style="text-shadow: 1px 1px wheat"
    >
      Contact Me
    </h2>

    <div class="grid grid-cols-1 md:grid-cols-5 gap-6 mt-6 animate-hidden">
      <!-- Skills (40%) -->
      <div class="md:col-span-2 rounded-lg">
        <h1
          class="text-2xl font-semibold mb-4 text-gray-900 animate-hidden"
          style="text-shadow: 1px 1px wheat"
        >
          Don't Be Shy to Contact Me 🐱‍🚀
        </h1>
        <p
          class="text-white text-600 animate-hidden mb-4 text-md text-justify text-shadow: 1px 1px wheat"
        >
          Come connect with me on social media
        </p>

        <div class="flex gap-4">
          <div v-for="sosmed in sosmeds" :key="sosmed.name" class="flex">
            <a
              :href="sosmed.url"
              target="_blank"
              class="bg-white hover:bg-blue-900 text-white p-2 rounded-full hover:bg-gray-800 transition duration-300"
              style="
                text-shadow: 1px 1px wheat;
                color: aliceblue;
                text-decoration: none;
              "
            >
              <img :src="sosmed.icon" :alt="sosmed.name" class="w-6 h-6" />
            </a>
          </div>
        </div>
      </div>

      <!-- Experience (60%) -->
      <div class="md:col-span-3 bg-gray-50 p-4 rounded-lg">
        <h3 class="text-xl font-semibold mb-4 text-gray-900">Email Me</h3>
        <!-- buatkan 2 kotak lagi -->
        <form action="">
          <div class="grid grid-cols-2 md:grid-cols-2 gap-6">
            <div class="col-span-1">
              <label for="name" class="text-gray-900">Name</label>
              <input
                type="text"
                id="name"
                name="name"
                placeholder="Please enter your name"
                class="w-full p-2 border border-gray-300 rounded-lg text-gray-900 hover:border-gray-500"
                :value="name"
                @input="name = $event.target.value"
              />
            </div>
            <div class="col-span-1">
              <label for="email" class="text-gray-900">
                Email
                <span class="text-red-500">*</span>
              </label>
              <input
                type="email"
                id="email"
                name="email"
                placeholder="Please enter your email"
                required
                class="w-full p-2 border border-gray-300 rounded-lg text-gray-900 hover:border-gray-500"
                :value="email"
                @input="email = $event.target.value"
              />
            </div>

            <div class="col-span-2">
              <label for="subject" class="text-gray-900">Subject</label>
              <input
                type="text"
                id="subject"
                name="subject"
                placeholder="Please enter subject message"
                class="w-full p-2 border border-gray-300 rounded-lg text-gray-900 hover:border-gray-500"
                :value="subject"
                @input="subject = $event.target.value"
              />
            </div>
            <div class="col-span-2">
              <label for="message" class="text-gray-900"
                >Message <span class="text-red-500">*</span>
              </label>

              <textarea
                id="message"
                name="message"
                placeholder="Please enter your message"
                required
                class="w-full p-2 border border-gray-300 rounded-lg text-gray-900 hover:border-gray-500"
                :value="message"
                @input="message = $event.target.value"
              ></textarea>
            </div>
            <div class="col-span-2">
              <button
                type="submit"
                class="w-full bg-blue-500 hover:bg-blue-600 text-white p-2 rounded-lg transition duration-300 hover:shadow-lg"
                style="text-shadow: 1px 1px wheat"
                @click.prevent="sendEmail"
              >
                Send
              </button>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
  <div class="loading" :style="isLoading ? '' : 'display: none;'">
    <div class="spinner"></div>
    <p>&nbsp;Sending email...</p>
  </div>
</template>

<style scoped>
.loading {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
  color: white;
  font-size: 2rem;
  font-weight: bold;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  animation: fadeIn 0.5s ease-in-out;
  text-align: center;
}
.spinner {
  width: 50px;
  height: 50px;
  border: 5px solid rgba(0, 162, 255, 0.3);
  border-top: 5px solid rgba(221, 245, 2, 0.543);
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.bg-red {
  background-color: #fa0404;
}
.bg-orange {
  background-color: #f6ad55;
}
.bg-cyan {
  background-color: #4ecdc4;
}
.bg-black {
  background-color: #333333;
}
.bg-green {
  background-color: #2b9348;
}
.bg-pink {
  background-color: #ff6b6b;
}
.bg-purple {
  background-color: #9b5de5;
}
.animate-hidden {
  opacity: 0;
  transform: translateY(50px);
  transition: opacity 1s ease-out, transform 1s ease-out;
}

.animate-visible {
  opacity: 1;
  transform: translateY(0);
}
</style>
