<script setup>
import { ref, computed, onMounted } from "vue";

const idComponent = ref("projects");

// Data proyek dengan kategori
const projects = ref([
  {
    name: "Student Points Management System",
    description: "Web-app to manage student points built with Laravel",
    image: "http://fikrierha.rf.gd/img/point.png",
    source: "https://github.com/LALA09-erha/",
    type: "Web",
  },
  {
    name: "Data Processing, Web Scraping, Crawling, and Network Analysis",
    description:
      "Web to show data processing, web scraping, crawling, and network analysis with Python",
    image: "https://pbs.twimg.com/media/GiAOpQwbEAArmB3?format=jpg&name=large",
    source: "http://fikrierha.rf.gd/files/Lab%20-%20Grouping%20Data.html",
    type: "Data Analyst",
  },
  {
    name: "Lab - Grouping Data",
    description: "Web to show result of grouping data with SQL",
    image: "https://pbs.twimg.com/media/GiAL0jMbYAA7p9H?format=png&name=medium",
    source: "http://fikrierha.rf.gd/files/Lab%20-%20Grouping%20Data.html",
    type: "Data Analyst",
  },
  {
    name: "Website Profile Pagagan Village",
    description: "Web to show profile of Pagagan Village built with Blogger",
    image: "https://pbs.twimg.com/media/GbEM_KAbQAMB58w?format=jpg&name=large",
    source: "https://www.desapagagan.my.id/",
    type: "Web",
  },
  {
    name: "Data Processing, Classification, Clustering, Regression, and Medical Case Studies",
    description:
      "Web to show data processing, classification, clustering, regression, and medical case studies with Python",
    image: "https://pbs.twimg.com/media/GiAPBl2awAAfJUT?format=jpg&name=large",
    source: "https://lala09-erha.github.io/datamining/intro.html",
    type: "Data Analyst",
  },
  {
    name: "Book Store",
    description: "Web-app to manage book store built with PHP Native",
    image: "http://fikrierha.rf.gd/img/book.jpg",
    source: "https://bookstoreppl.000webhostapp.com/",
    type: "Web",
  },
  {
    name: "Lab - Combining Tables",
    description: "Web to show result of combining tables with SQL",
    image: "https://pbs.twimg.com/media/GiANQujbAAAvag4?format=jpg&name=medium",
    source: "http://fikrierha.rf.gd/files/Lab%20-%20Menggabungkan%20Tabel.html",
    type: "Data Analyst",
  },
  {
    name: "Bacre System",
    description:
      "Web app to manage communication between security and information systems, built with Express.js.",
    image: "http://fikrierha.rf.gd/img/bacre.png",
    source: "https://github.com",
    type: "Web",
  },
  {
    name: "Lab - Ordering and Limiting",
    description: "Web to show result of ordering and limiting with SQL",
    image: "https://pbs.twimg.com/media/GiANgdjaQAImVsM?format=jpg&name=medium",
    source:
      "http://fikrierha.rf.gd/files/Lab%20-%20Ordering%20and%20Limiting.html",
    type: "Data Analyst",
  },
  {
    name: "System Absensi",
    description: "Web-app to manage student points built with Laravel",
    image: "http://fikrierha.rf.gd/img/absen.jpg",
    source: "https://github.com/LALA09-erha/",
    type: "Web",
  },
  {
    name: "Lab - SQL Around the World",
    description: "Web to show result of SQL around the world",
    image: "https://pbs.twimg.com/media/GiANrL0bcAADlMy?format=png&name=medium",
    source:
      "http://fikrierha.rf.gd/files/Lab%20-%20SQL%20Around%20the%20World.html",
    type: "Data Analyst",
  },
  {
    name: "System Inventary And Payroll",
    description: "Web-app to manage student points built  With Expess.JS",
    image: "http://fikrierha.rf.gd/img/payroll.jpg",
    source: "https://github.com/LALA09-erha/",
    type: "Web",
  },
  {
    name: "Lab - Successful Movies",
    description: "Web to show result of successful movies with SQL",
    image: "https://pbs.twimg.com/media/GiAOCqeagAAOvEt?format=png&name=medium",
    source: "http://fikrierha.rf.gd/files/Lab%20-%20Successful%20Movies.html",
    type: "Data Analyst",
  },
  {
    name: "System predict heart disease",
    description: "Web-app to predict heart disease built with Streamlit",
    source: "https://prediksipenyakitjantung.streamlit.app/",
    image: "http://fikrierha.rf.gd/img/jantung.jpg",
    type: "Data Analyst",
  },
  {
    name: "System Inventary and office administration",
    description: "Web-app to manage student points built with Laravel",
    image: "http://fikrierha.rf.gd/img/admin.jpg",
    source: "https://github.com/LALA09-erha/",
    type: "Web",
  },
  {
    name: "System predict beer production",
    description: "Web-app to predict beer production built with Streamlit",
    source: "https://beermanufacturing.streamlit.app/",
    image: "http://fikrierha.rf.gd/img/beer.jpg",
    type: "Data Analyst",
  },
  {
    name: "Application Android (Sholat.id)",
    description: "Android app to show schedule of sholat With React Native",
    source: "https://github.com/LALA09-erha/",
    image: "http://fikrierha.rf.gd/img/solat.jpg",
    type: "Data Analyst",
  },
  {
    name: "System predict shares",
    description: "Web-app to predict shares built with Streamlit",
    source: "https://bukitdarmoproperty.streamlit.app/",
    image: "http://fikrierha.rf.gd/img/saham.jpg",
    type: "Data Analyst",
  },
  {
    name: "Bot Discord (CocoPou)",
    description:
      "Bot discord to show information about youtube notification and football schedule",
    image: "http://fikrierha.rf.gd/img/coco.png",
    source:
      "https://discord.com/oauth2/authorize?client_id=796771650677899275&permissions=8&scope=bot",
    type: "Data Analyst",
  },
  {
    name: "System Quiz Online",
    description: "Web-app to show quiz online built  With HTML,JavaScript,CSS",
    image: "http://fikrierha.rf.gd/img/quiz.jpg",
    source: "https://lala09-erha.github.io/HTML-QuizOnline/",
    type: "Web",
  },
  {
    name: "Bot Discord (ChikaBot)",
    description:
      "Bot discord to show information about youtube notification and football schedule",
    image: "http://fikrierha.rf.gd/img/cika.jpg",
    source:
      "https://discord.com/oauth2/authorize?client_id=1101357310816829510&permissions=8&scope=bot",
    type: "Data Analyst",
  },
  {
    name: "System Management Coffee Shop",
    description: "Web-app to manage coffee shop built  With Codeigniter 4",
    image: "http://fikrierha.rf.gd/img/warkop.png",
    source: "https://github.com/LALA09-erha/",
    type: "Web",
  },
]);

// Filter aktif, default 'All'
const selectedType = ref("All");

// Menghitung proyek berdasarkan kategori yang dipilih
const filteredProjects = computed(() => {
  if (selectedType.value === "All") return projects.value;
  return projects.value.filter(
    (project) => project.type === selectedType.value
  );
});

// Fungsi untuk mengubah filter
const setFilter = (type) => {
  selectedType.value = type;
};

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
  <div class="container mx-auto p-6 w-full" :id="idComponent">
    <h2
      class="text-3xl font-bold text-gray-900 text-right mb-4 animate-hidden hover:text-white transition duration-300"
      style="text-shadow: 1px 1px wheat"
    >
      My Projects
    </h2>

    <!-- Filter Buttons -->
    <div class="flex space-x-3 mb-6 justify-center animate-hidden">
      <button
        v-for="type in ['All', 'Web', 'Data Analyst']"
        :key="type"
        @click="setFilter(type)"
        class="px-4 py-2 rounded-lg transition font-semibold"
        style="background-color: aliceblue"
        :class="{
          'text-black': selectedType !== type,
          'text-orange-600': selectedType === type,
        }"
      >
        {{ type }}
      </button>
    </div>

    <!-- Grid dengan 4 kolom -->
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 mt-6">
      <div
        v-for="(project, index) in filteredProjects"
        :key="index"
        class="bg-white p-4 rounded-lg shadow-lg max-w-full transition-transform transform hover:scale-105 hover:text-white transition duration-300"
      >
        <div class="relative group">
          <img
            :src="project.image"
            :alt="project.name"
            class="w-full h-48 object-cover rounded-lg"
          />
          <!-- Overlay & Tombol hanya muncul saat hover -->
          <div
            class="absolute inset-0 bg-black bg-opacity-60 rounded-lg flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300"
          >
            <a
              :href="project.image"
              target="_blank"
              class="bg-blue-600 px-4 py-2 rounded-lg mx-2 hover:bg-blue-800 transition"
              style="color: aliceblue"
              >View Image</a
            >
            <a
              :href="project.source"
              target="_blank"
              class="bg-green-600 px-4 py-2 rounded-lg mx-2 hover:bg-green-800 transition"
              style="color: aliceblue"
              >View Source</a
            >
          </div>
        </div>
        <div class="mt-4">
          <h3 class="text-xl font-semibold text-gray-900">
            {{ project.name }}
          </h3>
          <p class="text-gray-600">{{ project.description }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
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
