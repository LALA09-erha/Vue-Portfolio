<script setup>
const year = new Date().getFullYear();
</script>

<template>
  <footer class="footer-container">
    <div class="footer-content">
      <p class="text-sm">
        &copy; {{ year }} Fikri Ainun Najib. All rights reserved.
      </p>
      <nav class="footer-nav">
        <a href="#about">About</a>
        <a href="#projects">Projects</a>
        <a href="#contact">Contact</a>
      </nav>
    </div>
  </footer>
</template>

<style scoped>
.footer-container {
  background-color: #1a1a1a;
  color: #ffffff;
  padding: 1rem 0;
  text-align: center;
  width: 100%;
  position: relative;
}

.footer-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

.footer-nav {
  display: flex;
  gap: 15px;
}

.footer-nav a {
  color: #ffffff;
  text-decoration: none;
  font-size: 0.9rem;
  transition: color 0.3s ease;
}

.footer-nav a:hover {
  color: #ffcc00;
}

.social-icons {
  display: flex;
  gap: 10px;
}

.social-icons img {
  width: 24px;
  height: 24px;
  transition: transform 0.3s ease;
}

.social-icons img:hover {
  transform: scale(1.2);
}
</style>
