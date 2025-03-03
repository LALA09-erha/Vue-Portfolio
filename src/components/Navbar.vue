<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const isScrolled = ref(false);
const isAtTop = ref(true);
const isMenuOpen = ref(false);

let activeMenu = ref("/");

const handleScroll = () => {
  const scrollY = window.scrollY;
  isScrolled.value = scrollY > 50; // Muncul saat user scroll sedikit
  isAtTop.value = scrollY === 0; // Hilang jika kembali ke atas
};

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const closeMenu = (menu) => {
  activeMenu.value = menu;
  isMenuOpen.value = false;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<template>
  <nav :class="['navbar', { 'navbar-visible': isScrolled && !isAtTop }]">
    <div class="navbar-container">
      <div class="navbar-logo">
        <a href="#home" @click="closeMenu('home')">
          <img
            src="https://www.freeiconspng.com/thumbs/gaming-logo/cool-black-gaming-logo--bad-character-png-free-download-4.png"
            alt="Logo"
          />
        </a>
      </div>
      <ul class="navbar-menu" :class="{ 'navbar-menu-active': isMenuOpen }">
        <li>
          <a
            :class="{ 'active-nav': activeMenu === 'about' }"
            href="#about"
            @click="closeMenu('about')"
            >About</a
          >
        </li>
        <li>
          <a
            :class="{ 'active-nav': activeMenu === 'skills' }"
            href="#skills"
            @click="closeMenu('skills')"
            >Skills</a
          >
        </li>
        <li>
          <a
            :class="{ 'active-nav': activeMenu === 'projects' }"
            href="#projects"
            @click="closeMenu('projects')"
            >Projects</a
          >
        </li>
        <li>
          <a
            :class="{ 'active-nav': activeMenu === 'contact' }"
            href="#contact"
            @click="closeMenu('contact')"
            >Contact Me</a
          >
        </li>
      </ul>
      <div class="navbar-hamburger" @click="toggleMenu">
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>
  </nav>
</template>

<style scoped>
/* Navbar Styling */
.navbar {
  position: fixed;
  top: -80px;
  left: 50%;
  transform: translateX(-50%);
  width: 350px;
  background: rgba(255, 255, 255, 0.9);
  border-radius: 50px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  transition: top 0.5s ease-in-out, opacity 0.5s ease-in-out;
  padding: 10px;
  text-align: center;
  opacity: 0;
  z-index: 1000;
}

.navbar-visible {
  top: 20px;
  opacity: 1;
}

.navbar-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.navbar-logo img {
  height: 30px;
  border-radius: 50%;
}

/* Navbar Menu */
.navbar-menu {
  display: flex;
  gap: 1rem;
  list-style: none;
}

.navbar-menu li a {
  text-decoration: none;
  color: #333;
  font-weight: bold;
  transition: color 0.3s;
}

.navbar-menu li a:hover {
  color: #6200ea;
}

.navbar-menu li a.active-nav {
  color: #6200ea;
  font-weight: bold;
}

/* Hamburger Menu */
.navbar-hamburger {
  display: none;
  flex-direction: column;
  cursor: pointer;
  gap: 5px;
}

.navbar-hamburger span {
  width: 25px;
  height: 3px;
  background: #333;
  transition: transform 0.3s, opacity 0.3s;
}

/* Responsive */
@media (max-width: 768px) {
  .navbar {
    width: 80%;
  }

  .navbar-menu {
    position: absolute;
    top: 100%;
    left: 50%;
    transform: translateX(-50%);
    background: rgba(255, 255, 255, 0.95);
    width: 100%;
    border-radius: 10px;
    padding: 1rem 0;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
    opacity: 0;
    transition: opacity 0.3s ease-in-out;
    pointer-events: none;
  }

  .navbar-menu-active {
    opacity: 1;
    pointer-events: auto;
  }

  .navbar-hamburger {
    display: flex;
  }
}
</style>
