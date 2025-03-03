<script setup>
import { ref, onMounted } from "vue";

const idComponent = ref("skills");

const skills = ref([
  { name: "HTML", level: 90, color: "bg-red" },
  { name: "CSS (Bootsrap & Tailwind)", level: 80, color: "bg-orange" },
  {
    name: "JavaScript {Vue.js, React.js, Express.js, Hapi.js and Node.js}",
    level: 85,
    color: "bg-cyan",
  },
  { name: "PHP (Laravel and Codeigniter)", level: 70, color: "bg-black" },
  {
    name: "Python (Django, Flask and Streamlit)",
    level: 75,
    color: "bg-green",
  },
  { name: "Go (Gin Framework)", level: 60, color: "bg-pink" },
  { name: "SQL (MySQL, PostgreSQL, SQLite)", level: 80, color: "bg-purple" },
  {
    name: "Others (Docker, Git, Nginx, Postman, etc)",
    level: 70,
    color: "bg-red",
  },
]);

const experience = ref([
  {
    company: "PT Mitra Perdagangan Indonesia Tbk",
    position: "Backend Developer (Internship)",
    duration: "Jan 2023 - Feb 2023",
  },
  {
    company: "Involuntir",
    position: "Backend Developer (Internship)",
    duration: "Nov 2024 - Feb 2025",
  },
  {
    company: "Indosat Ooredoo Hutchison Digital Camp",
    position: "Backend Developer Trainee",
    duration: "Sep 2024 - Mar 2025",
  },
  {
    company: "Are there any opportunities?",
    position: "mailto:erhafikri@gmail.com",
    duration: "",
  },
]);

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
      Skills & Experience
    </h2>

    <div class="grid grid-cols-1 md:grid-cols-5 gap-6 mt-6 animate-hidden">
      <!-- Skills (40%) -->
      <div class="md:col-span-2 bg-gray-100 p-4 rounded-lg">
        <h3 class="text-xl font-semibold mb-4 text-gray-900">My Skills</h3>
        <div
          v-for="skill in skills"
          :key="skill.name"
          class="mb-2 hover:shadow-lg transition duration-300"
        >
          <div class="flex justify-between items-center mb-1">
            <span class="text-gray-600 hover:text-blue-500">{{
              skill.name
            }}</span>
            <span class="text-gray-600">{{ skill.level }}%</span>
          </div>
          <div
            class="h-2 bg-gray-200 rounded-full"
            :class="skill.color"
            :style="{ width: skill.level + '%' }"
          ></div>
        </div>
      </div>

      <!-- Experience (60%) -->
      <div class="md:col-span-3 bg-gray-50 p-4 rounded-lg animate-hidden">
        <h3 class="text-xl font-semibold mb-4 text-gray-900">Experience</h3>
        <!-- buatkan 2 kotak lagi -->
        <div class="grid grid-cols-2 md:grid-cols-2 gap-6">
          <div
            v-for="exp in experience"
            :key="exp.company"
            class="mb-4 animate-hidden bg-white p-4 rounded-lg shadow-md hover:shadow-lg transition duration-300"
          >
            <div class="mb-2">
              <span
                class="text-gray-600 font-bold text-lg hover:text-orange-500"
                style="font-family: serif"
                >{{ exp.company }}</span
              >
              <hr class="border-gray-300" />
              <div class="text-gray-600 text-sm" style="font-family: serif">
                {{ exp.duration }}
              </div>

              <span
                class="text-gray-600 text-md font-bold"
                v-if="!exp.position.includes('mailto:')"
                style="font-family: serif"
                >{{ exp.position }}</span
              >
              <a
                :href="exp.position"
                target="_blank"
                v-else
                class="text-gray-600 text-md font-bold text-decoration-none cursor-pointer"
                style="font-family: serif; color: black"
                >Please contact me via email :
                <span class="text-blue-500">{{
                  exp.position.replace("mailto:", "")
                }}</span>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
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
