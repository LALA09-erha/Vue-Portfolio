<script setup>
import { ref, onMounted } from "vue";

const idComponent = ref("about");
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
  <div
    class="hero h-screen w-full flex items-center justify-center relative overflow-hidden px-6 animate-hidden"
    :id="idComponent"
  >
    <div
      class="absolute inset-0 bg-gradient-to-r from-purple-400 via-blue-500 to-indigo-600 opacity-30"
    />
    <section class="about-me">
      <div class="container animate-hidden">
        <!-- Foto 30%  agar tidak bisa di drag / di klik-->
        <div class="image-container animate-hidden select-none noselect">
          <img
            src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExanBjY2wzcjlycno5emJzYXNrcWhoeGQyamtyOXR1b3U3Z3FkcSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/eVFNEZreqJaPKXahr5/giphy.gif"
            alt="Your Photo"
            class="no-drag"
            draggable="false"
            oncontextmenu="return false;"
            onmousedown="return false;"
          />
        </div>

        <!-- Teks 70% -->
        <div class="text-container">
          <h2>About Me</h2>
          <p class="text-justify">
            I am a website developer With extensive experience and deep
            understanding of information technology, I have successfully built
            various innovative and efficient software solutions. As a
            results-oriented professional, I possess strong analytical skills to
            design and implement complex technical solutions, ensuring that the
            projects I work on always meet high-quality standards.
          </p>

          <!-- 4 Kolom -->
          <div class="grid-container animate-hidden">
            <div class="grid-item">
              <h3
                class="flex items-center justify-center text-center text-xl font-bold text-gray-800 text-opacity-80"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  class="size-6 text-inline"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M3.75 3v11.25A2.25 2.25 0 0 0 6 16.5h2.25M3.75 3h-1.5m1.5 0h16.5m0 0h1.5m-1.5 0v11.25A2.25 2.25 0 0 1 18 16.5h-2.25m-7.5 0h7.5m-7.5 0-1 3m8.5-3 1 3m0 0 .5 1.5m-.5-1.5h-9.5m0 0-.5 1.5M9 11.25v1.5M12 9v3.75m3-6v6"
                  />
                </svg>
                Experience
              </h3>
              <p>4+ Years in Web Development and Programming</p>
            </div>
            <div class="grid-item">
              <h3
                class="flex items-center justify-center text-center text-xl font-bold text-gray-800 text-opacity-80"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  class="size-6"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M6.429 9.75 2.25 12l4.179 2.25m0-4.5 5.571 3 5.571-3m-11.142 0L2.25 7.5 12 2.25l9.75 5.25-4.179 2.25m0 0L21.75 12l-4.179 2.25m0 0 4.179 2.25L12 21.75 2.25 16.5l4.179-2.25m11.142 0-5.571 3-5.571-3"
                  />
                </svg>

                Projects
              </h3>
              <p>Developed 10+ projects</p>
            </div>
            <div class="grid-item">
              <h3
                class="flex items-center justify-center text-center text-xl font-bold text-gray-800 text-opacity-80"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  class="size-6"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M16.5 18.75h-9m9 0a3 3 0 0 1 3 3h-15a3 3 0 0 1 3-3m9 0v-3.375c0-.621-.503-1.125-1.125-1.125h-.871M7.5 18.75v-3.375c0-.621.504-1.125 1.125-1.125h.872m5.007 0H9.497m5.007 0a7.454 7.454 0 0 1-.982-3.172M9.497 14.25a7.454 7.454 0 0 0 .981-3.172M5.25 4.236c-.982.143-1.954.317-2.916.52A6.003 6.003 0 0 0 7.73 9.728M5.25 4.236V4.5c0 2.108.966 3.99 2.48 5.228M5.25 4.236V2.721C7.456 2.41 9.71 2.25 12 2.25c2.291 0 4.545.16 6.75.47v1.516M7.73 9.728a6.726 6.726 0 0 0 2.748 1.35m8.272-6.842V4.5c0 2.108-.966 3.99-2.48 5.228m2.48-5.492a46.32 46.32 0 0 1 2.916.52 6.003 6.003 0 0 1-5.395 4.972m0 0a6.726 6.726 0 0 1-2.749 1.35m0 0a6.772 6.772 0 0 1-3.044 0"
                  />
                </svg>
                Hobby
              </h3>
              <p>Playing Video Games & Swimming</p>
            </div>
            <div class="grid-item">
              <h3
                class="flex items-center justify-center text-center text-xl font-bold text-gray-800 text-opacity-80"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  class="size-6"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M15 9h3.75M15 12h3.75M15 15h3.75M4.5 19.5h15a2.25 2.25 0 0 0 2.25-2.25V6.75A2.25 2.25 0 0 0 19.5 4.5h-15a2.25 2.25 0 0 0-2.25 2.25v10.5A2.25 2.25 0 0 0 4.5 19.5Zm6-10.125a1.875 1.875 0 1 1-3.75 0 1.875 1.875 0 0 1 3.75 0Zm1.294 6.336a6.721 6.721 0 0 1-3.17.789 6.721 6.721 0 0 1-3.168-.789 3.376 3.376 0 0 1 6.338 0Z"
                  />
                </svg>

                Education
              </h3>
              <p>Bachelor's in Informatics Engineering</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.hero {
  user-select: none;
  -moz-user-select: none;
  -khtml-user-select: none;
  -webkit-user-select: none;
  -o-user-select: none;
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
.animate-fade-in {
  animation: fadeIn 1.5s ease-out;
}

.animate-slide-in {
  animation: slideIn 1.5s ease-out;
}

.about-me {
  padding: 50px 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  display: flex;
  width: 100%;
  max-width: 1200px;
}

.image-container {
  flex: 0 0 30%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.image-container img {
  width: 100%;
  border-radius: 15px;
}

.text-container {
  flex: 0 0 70%;
  padding-left: 30px;
}

.grid-container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
  margin-top: 20px;
}

.grid-item {
  background: #f3f3f3;
  color: black;
  padding: 15px;
  border-radius: 10px;
  text-align: center;
}

h2 {
  font-size: 24px;
}

@media (max-width: 768px) {
  .container {
    flex-direction: column;
    text-align: center;
  }

  .image-container {
    display: none;
  }

  .text-container {
    font-size: 15px;
    padding-left: 0;
  }

  .grid-container {
    grid-template-columns: 1fr;
    gap: 10px;
    margin-top: 10px;
  }

  .grid-item {
    padding: 10px;
  }
}
</style>
