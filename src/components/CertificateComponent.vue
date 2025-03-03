<script setup>
import { ref, computed } from "vue";

const certificates = ref([
  {
    title: "Cloud Practitioner Essentials (Basic AWS Cloud Learning)",
    provider: "Dicoding Indonesia",
    link: "https://drive.google.com/file/d/1U_1vq1ttsj6MuR8hwBLExzEmbduk4Km7/view?usp=sharing",
  },
  {
    title: "Fundamentals of Artificial Intelligence",
    provider: "Dicoding Indonesia",
    link: "https://drive.google.com/file/d/1FvAjWr-U0sRkue9A87xf4vcGafnFpcNc/view?usp=sharing",
  },
  {
    title: "Docker for Beginners",
    provider: "CODEPOLITAN",
    link: "https://drive.google.com/file/d/1TBOJJUnRegFaMVAmltN8OtjB-KYJGCFB/view?usp=sharing",
  },
  {
    title: "Go-Lang for Beginners",
    provider: "CODEPOLITAN",
    link: "https://drive.google.com/file/d/1DOTT_tnA03TE3_fQnThkgyuvBbPuP53w/view?usp=sharing",
  },
  {
    title: "Responsive Web Design",
    provider: "freeCodeCamp",
    link: "https://freecodecamp.org/certification/cocopou/responsive-web-design",
  },
  {
    title: "Fundamentals of JavaScript Programming",
    provider: "Dicoding Indonesia",
    link: "https://drive.google.com/file/d/1naTGpawDedTXOJxC7hoP4w6nkLGNCyXZ/view?usp=sharing",
  },
  {
    title: "Building Back-End Applications for Beginners",
    provider: "Dicoding Indonesia",
    link: "https://drive.google.com/file/d/1wPIwTsuObN_gTHQd9Oabq_clYPF0Wq-7/view?usp=sharing",
  },
  {
    title: "Basics of Python Data Wrangling",
    provider: "Great Learning",
    link: "https://drive.google.com/file/d/1MeBivs98vabP30O6EEO1VowfQRGgeHnQ/view?usp=sharing",
  },
  {
    title: "Data Preprocessing with Python",
    provider: "Great Learning",
    link: "https://drive.google.com/file/d/1Z0lYzEuHv5Mnh1K2erUnbYiqXVf_BHWJ/view?usp=sharing",
  },
  {
    title: "Front-End Development - HTML",
    provider: "Great Learning",
    link: "https://drive.google.com/file/d/1X19XATCHX1t4jONl09O7Qfe65nl3Y_3C/view?usp=sharing",
  },
  {
    title: "Introduction to Exploratory Data Analysis with Excel",
    provider: "Great Learning",
    link: "https://drive.google.com/file/d/1KLMRPsbQLllBjbnyxU42DF2N3ygZIf5U/view?usp=sharing",
  },
  {
    title: "Introduction to Databases and SQL",
    provider: "Great Learning",
    link: "https://drive.google.com/file/d/1x2iHWslEbAB9Fi5Rf26tPmBzMSRDGrTN/view?usp=sharing",
  },
  {
    title: "Introduction to Machine Learning (US)",
    provider: "Great Learning",
    link: "https://drive.google.com/file/d/1GUtBdQtHy0DPCpZV15ZvAXDgKY0q2mee/view?usp=sharing",
  },
  {
    title: "Introduction to NoSQL",
    provider: "Great Learning",
    link: "https://drive.google.com/file/d/1x3-Tua8cX_1kVPQVCJSfHLX_xMOcW7gP/view?usp=sharing",
  },
  {
    title: "MySQL Tutorial",
    provider: "Great Learning",
    link: "https://drive.google.com/file/d/1hqncCyWngflmnysdfdbW0LwlTaUZoNbX/view?usp=sharing",
  },
  {
    title: "Python Foundations",
    provider: "Great Learning",
    link: "https://drive.google.com/file/d/1aPR_JwADWW3UdrRkn9fNqScBvx7UFfKC/view?usp=sharing",
  },
  {
    title: "Python Fundamentals for Beginners",
    provider: "Great Learning",
    link: "https://drive.google.com/file/d/13X3s3E3kNbRKrUctYc-nzhX-4TaJEJlV/view?usp=sharing",
  },
  {
    title: "Python for Machine Learning and Data Science",
    provider: "Great Learning",
    link: "https://drive.google.com/file/d/1nwp49hgCOrxM2VrfjRJJThI8RxCzt1vK/view?usp=sharing",
  },
  {
    title: "CCNAv7: Introduction to Networks",
    provider: "Cisco",
    link: "https://drive.google.com/file/d/1TUVuP9SB0RGiTDOSCdoXkQic2CV1UAP4/view?usp=sharing",
  },
]);

const showAllCertificates = () => {
  window.open(
    "https://drive.google.com/drive/folders/1_5ryr8cOULxtP1zXC014Tr5qeT9Yw-4-?usp=sharing",
    "_blank"
  );
};

// Duplikasi daftar sertifikat agar looping terlihat seamless
const duplicatedCertificates = computed(() => [
  ...certificates.value,
  ...certificates.value,
]);
</script>

<template>
  <div
    class="container mx-auto p-1 w-full items-center justify-center flex flex-col"
    :id="idComponent"
    style="width: 100%; max-width: 100%"
  >
    <h2
      class="text-3xl font-bold text-gray-900 text-center mb-4 animate-hidden hover:text-white transition duration-300"
      style="text-shadow: 1px 1px wheat"
    >
      My Certificates
    </h2>
    <div class="marquee-container absolute top-0 left-0 right-0">
      <div class="marquee">
        <div class="marquee-content text-center">
          <span v-for="(cert, index) in duplicatedCertificates" :key="index">
            <a :href="cert.link" target="_blank" class="marquee-item">
              {{ cert.title }}
            </a>
            <span class="text-lg" style="font-size: 40px"
              >&nbsp;&nbsp;&nbsp;•&nbsp;</span
            >
            <p>
              {{ cert.provider }}
            </p>
          </span>
        </div>
      </div>
    </div>

    <button
      class="btn btn-primary mt-4 align-center mx-auto animate-hidden hover:animate-pulse transition duration-300"
      style="background-color: #ff5722"
      @click="showAllCertificates"
    >
      See All Certificates
    </button>
  </div>
</template>

<style scoped>
.marquee-container {
  overflow: hidden;
  white-space: nowrap;
  position: relative;
  width: 100%;
  padding: 10px 0;
}

.marquee {
  display: flex;
  width: max-content;
  animation: marquee-scroll 120s linear infinite;
}

.marquee-content {
  display: flex;
  gap: 20px;
}

@keyframes marquee-scroll {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(-50%);
  }
}

@media screen and (max-width: 768px) {
  .marquee-item {
    font-size: 0.5rem;
  }
}

@media screen and (max-width: 480px) {
  .marquee-item {
    font-size: 0.5rem;
  }
}

.marquee-item {
  color: white;
  text-decoration: none;
  font-weight: bold;
  font-size: 2rem;
}

.marquee-item:hover {
  text-decoration: underline;
  cursor: pointer;
  color: #000;
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
