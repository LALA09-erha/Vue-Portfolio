<script setup>
import { ref, onMounted, onUnmounted, nextTick } from "vue";
import HeroComponent from "./components/HeroComponent.vue";
import Navbar from "./components/Navbar.vue";
import ProfileComponent from "./components/ProfileComponent.vue";
import SkillComponent from "./components/SkillComponent.vue";
import ProjectComponent from "./components/ProjectComponent.vue";
import CertificateComponent from "./components/CertificateComponent.vue";
import ContactCompenent from "./components/ContactComponent.vue";
import FooterComponent from "./components/FooterComponent.vue";
const isLoading = ref(true);
const isFadingOut = ref(false);
const isScrolled = ref(false);
const isAtTop = ref(true);

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: "smooth" });
};

const scrollToHash = () => {
  if (window.location.hash) {
    const targetId = window.location.hash.substring(1); // Remove "#"
    try {
      nextTick(() => {
        const element = document.getElementById(targetId);
        if (element) {
          element.scrollIntoView({ behavior: "smooth" });
        } else {
          history.replaceState(null, null, " ");
        }
      });
    } catch (e) {
      console.error(e);
    }
  }
};

const handleScroll = () => {
  const scrollY = window.scrollY;
  isScrolled.value = scrollY > 50;
  isAtTop.value = scrollY === 0;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
  scrollToHash();
  window.addEventListener("hashchange", scrollToHash);

  setTimeout(() => {
    isFadingOut.value = true;
    setTimeout(() => {
      isLoading.value = false;
    }, 500);
  }, 1500);
});
</script>

<template>
  <transition name="fade">
    <div
      v-if="isLoading"
      class="loading-screen"
      :class="{ 'fade-out': isFadingOut }"
    >
      <div class="spinner"></div>
    </div>
  </transition>
  <div
    v-if="!isLoading"
    class="bg-gradient-to-r from-purple-400 via-blue-500 to-indigo-600 text-white opacity-90"
  >
    <Navbar />
    <HeroComponent />
    <ProfileComponent />
    <SkillComponent />
    <ProjectComponent />
    <CertificateComponent />
    <ContactCompenent />
    <FooterComponent />
  </div>
  <!-- Tombol Back to Top -->
  <button v-if="isScrolled" class="back-to-top" @click="scrollToTop">▲</button>
</template>

<style scoped>
/* Tombol Back to Top */
.back-to-top {
  z-index: 1000;
  position: fixed;
  bottom: 20px;
  right: 20px;
  /* buatkan gradien */
  background: linear-gradient(135deg, #3669bf 0%, #cc5fca 100%);
  color: white;
  border: none;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  font-size: 20px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
  transition: opacity 0.3s, transform 0.3s;
}

.back-to-top:hover {
  transform: scale(1.1);
}
.loading-screen {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: #121212;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: opacity 0.5s ease-in-out;
}

.fade-out {
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.5s ease-in-out;
  z-index: -1;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.spinner {
  width: 50px;
  height: 50px;
  border: 5px solid rgba(240, 33, 255, 0.3);
  border-top: 5px solid rgba(79, 255, 223, 0.543);
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
