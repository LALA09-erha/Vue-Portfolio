<script setup>
import { ref, onMounted } from "vue";

// Data for the hero section
const name = ref("I'm");
const role = ref("Fikri Ainun Najib");
const description = ref(""); // Will be filled with typing effect
const typedText = ref("");
const idComponent = ref("home");
const textsToType = [
  "I am a Software Engineer.",
  "I am a Data Scientist.",
  "I am a Analysis System.",
  "I am a Content Writer.",
];
let currentTextIndex = 0;
let charIndex = 0;
let isDeleting = false;

// Social media links
const socialMedia = [
  {
    name: "LinkedIn",
    icon: "https://cdn2.iconfinder.com/data/icons/social-media-2285/512/1_Linkedin_unofficial_colored_svg-512.png",
    url: "https://www.linkedin.com/in/fikriainunnajib/",
  },
  {
    name: "Instagram",
    icon: "https://cdn2.iconfinder.com/data/icons/social-media-2285/512/1_Instagram_colored_svg_1-512.png",
    url: "https://www.instagram.com/fikri_erha/",
  },
  {
    name: "Blog",
    icon: "https://cdn4.iconfinder.com/data/icons/iconsimple-logotypes/512/blogger-256.png",
    url: "https://kangtunjuk.blogspot.com/",
  },
  {
    name: "GitHub",
    icon: "https://pngimg.com/d/github_PNG40.png",
    url: "https://github.com/LALA09-erha/",
  },
];

// Function for the typing effect
const typeText = () => {
  const currentText = textsToType[currentTextIndex];
  if (!isDeleting) {
    typedText.value = currentText.slice(0, charIndex + 1);
    charIndex++;
    if (charIndex === currentText.length) {
      isDeleting = true;
      setTimeout(typeText, 2000); // Pause after finishing typing
    } else {
      setTimeout(typeText, 100); // Typing speed
    }
  } else {
    typedText.value = currentText.slice(0, charIndex - 1);
    charIndex--;
    if (charIndex === 0) {
      isDeleting = false;
      currentTextIndex = (currentTextIndex + 1) % textsToType.length; // Move to the next text
      setTimeout(typeText, 500); // Pause before starting to type again
    } else {
      setTimeout(typeText, 50); // Deleting speed
    }
  }
};

const sendEmail = () => {
  const projects = document.getElementById("contact");
  if (projects) {
    projects.scrollIntoView({ behavior: "smooth" });
  }
};

const downloadCv = () => {
  window.open(
    "https://drive.google.com/drive/u/8/folders/1qvHqOsew-QMQnExzJuJ55KNyUvzreiBk"
  );
};

// Run the typing effect when the component is mounted
onMounted(() => {
  typeText();
});
</script>

<template>
  <div
    class="hero h-screen w-full flex items-center justify-center relative overflow-hidden"
    :id="idComponent"
  >
    <div
      class="absolute inset-0 bg-gradient-to-r from-purple-400 via-blue-500 to-indigo-600 opacity-30"
    />
    <div
      class="hero-content flex flex-col md:flex-row items-center gap-8 relative z-10"
    >
      <!-- Profile Picture -->
      <div
        class="w-48 h-48 md:w-64 md:h-64 rounded-full overflow-hidden border-4 border-primary shadow-lg animate-fade-in picture-profile"
      >
        <img
          src="https://pbs.twimg.com/media/Gj49d4FbQAArIT9?format=png&name=small"
          alt="Profile Picture"
          class="w-full h-full object-cover"
        />
      </div>

      <!-- Text and Buttons -->
      <div class="text-center md:text-left max-w-2xl animate-slide-in">
        <!-- Name -->
        <h6 class="text-xl md:text-2xl font-semibold text-primary">
          <span
            class="text-secondary font-bold animate-fade-in text-yellow-400 border-b-4 border-yellow-400"
            >Hello,</span
          >
          {{ name }}
        </h6>

        <!-- Role -->
        <h1
          class="text-6xl md:text-6xl font-bold text-secondary mb-6 text-name"
        >
          {{ role }}
        </h1>

        <!-- Description with Typing Effect -->
        <p
          class="text-lg md:text-xl text-white mb-8 h-12"
          style="font-family: monospace"
        >
          {{ typedText }}<span class="blinking-cursor">|</span>
        </p>

        <!-- Action Buttons -->
        <div class="flex gap-4 justify-center md:justify-start mb-8">
          <button
            class="btn btn-primary hover:scale-105 transition-transform"
            @click="downloadCv"
          >
            Download CV
          </button>
          <button
            class="btn btn-outline btn-secondary hover:scale-105 transition-transform"
            @click="sendEmail"
          >
            Contact Me
          </button>
        </div>

        <!-- Social Media Buttons -->
        <div class="flex gap-4 justify-center md:justify-start">
          <a
            v-for="social in socialMedia"
            :key="social.name"
            :href="social.url"
            target="_blank"
            class="btn btn-ghost btn-circle hover:scale-110 transition-transform"
            :title="social.name"
          >
            <img
              :src="social.icon"
              alt="Social Media Icon"
              class="w-6 h-6 rounded"
            />
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Animations */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: scale(0.9);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

@keyframes slideIn {
  from {
    transform: translateY(20px);
    opacity: 0;
  }
  to {
    transform: translateY(0);
    opacity: 1;
  }
}

.animate-gradient {
  position: absolute;
  width: 100px;
  height: 100px;
  background: radial-gradient(
    circle,
    rgba(255, 255, 255, 0.5) 10%,
    transparent 80%
  );
  pointer-events: none;
  border-radius: 50%;
  transform: translate(-50%, -50%);
}

.animate-fade-in {
  animation: fadeIn 1.5s ease-out;
}

.animate-slide-in {
  animation: slideIn 1.5s ease-out;
}

/* Blinking cursor for typing effect */
.blinking-cursor {
  animation: blink 1s infinite;
}

/* Media queries for responsiveness */
@media screen and (max-width: 768px) {
  .text-name {
    font-size: 2rem;
  }
  .picture-profile {
    width: 150px;
    height: 150px;
  }
}

.picture-profile:hover {
  transform: scale(1.1);
  transition: transform 0.3s ease-in-out;
  cursor: pointer;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
}

@keyframes blink {
  0%,
  50% {
    opacity: 1;
  }
  51%,
  100% {
    opacity: 0;
  }
}
</style>
