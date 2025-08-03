<script setup>
import { ref } from 'vue'
import Navbar from './components/Navbar.vue'
import AboutPage from './components/AboutPage.vue'
import ProjectsPage from './components/ProjectsPage.vue'
import TestimonialsPage from './components/TestimonialsPage.vue'
import ContactPage from './components/ContactPage.vue'

// Pop art styled portfolio landing page
const currentPage = ref('home')

const navigateTo = (page) => {
  currentPage.value = page
}
</script>

<template>
  <div class="app-container">
    <!-- Navbar -->
    <Navbar :current-page="currentPage" @navigate="navigateTo" />

    <!-- Routed Pages -->
    <template v-if="currentPage === 'home'">
      <div class="pop-art-portfolio">
        <!-- Main Content -->
        <div id="landing-page">
          <div class="hero-section row">
            <div class="welcome-text col-md-6">
              <div class="welcome-text-container">
                <p>Welcome to </p>
                <h1 class="main-title">
                  <span class="title-line">MIKHAIL'S</span>
                  <span class="title-line">PORTFOLIO</span>
                </h1>
                <p class="tagline">
                  Creative Developer & Digital Artist
                </p>
                <div class="cta-section">
                  <button class="cta-button" @click="navigateTo('contact')">
                    <span class="button-text">GET IN TOUCH</span>
                  </button>
                </div>
              </div>
            </div>
            <div class="landing-image col-md-6">
              <img src="/src/assets/pop-art-cat.png" id="landing-image" alt="Pop Art Background" />
            </div>
          </div>
        </div>
      </div>
    </template>

    <AboutPage v-else-if="currentPage === 'about'" />
    <ProjectsPage v-else-if="currentPage === 'projects'" />
    <TestimonialsPage v-else-if="currentPage === 'testimonials'" @navigate="navigateTo" />
    <ContactPage v-else-if="currentPage === 'contact'" @go-back="navigateTo('home')" />
  </div>
</template>

<style scoped>
.app-container {
  width: 100vw;
  min-height: 100vh;
  overflow-x: hidden;
}

.landing-image.col-md-6 {
  display: flex;
  justify-content: start;
}

.welcome-text.col-md-6 {
  display: flex;
  flex-direction: column;
  justify-content: safe;
  align-items: end;
}

.pop-art-portfolio {
  position: relative;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  background-color: var(--bg-primary);
}

.content {
  position: relative;
  z-index: 3;
  display: flex;
  align-items: center;
  height: 100%;
  padding: 2rem;
  background: var(--bg-primary);
}

.hero-section {
  text-align: center;
  width: 100%;
  display: flex;
  height: 100%;
  align-content: center;
}

.main-title {
  font-size: clamp(3rem, 8vw, 8rem);
  font-weight: 900;
  line-height: 0.9;
  margin-bottom: 2rem;
  text-shadow:
    4px 4px 0 var(--pop-black),
    8px 8px 0 var(--pop-dark-gray),
    12px 12px 0 var(--pop-yellow);
  animation: titleFloat 3s ease-in-out infinite;
}

.title-line {
  display: block;
  transform: rotate(-2deg);
  transition: transform 0.3s ease;
  filter: drop-shadow(1px 5px 6px black);
}

.title-line:hover {
  transform: rotate(2deg) scale(1.05);
}

.tagline {
  font-size: clamp(1.2rem, 3vw, 2rem);
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 3rem;
  background: linear-gradient(45deg, var(--pop-black), var(--pop-dark-gray), var(--pop-gray));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.cta-section {
  margin-top: 3rem;
}

.cta-button {
  position: relative;
  padding: 1.5rem 3rem;
  font-size: 1.2rem;
  font-weight: 900;
  text-transform: uppercase;
  letter-spacing: 2px;
  border: var(--border-thick);
  color: var(--pop-dark-gray);
  cursor: pointer;
  transition: all var(--animation-fast) ease;
  box-shadow:
    8px 8px 0 var(--pop-dark-gray),
    16px 16px 0 var(--pop-gray);
  animation: buttonBounce 2s ease-in-out infinite;
}

.cta-button:hover {
  transform: translate(-4px, -4px);
  box-shadow:
    12px 12px 0 var(--pop-dark-gray),
    20px 20px 0 var(--pop-yellow);
  color: var(--pop-black);
}

.cta-button:active {
  transform: translate(0, 0);
}

.button-text {
  margin-right: 1rem;
}

#landing-page {
  height: 100vh;
}

#landing-image {
  width: 55%;
  height: 100%;
  object-fit: cover;
  filter: drop-shadow(9px 4px 0px var(--pop-yellow));
}

/* Floating Elements */
.floating-elements {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 2;
}

.floating-circle {
  position: absolute;
  border-radius: 50%;
  opacity: 0.7;
  animation: float 6s ease-in-out infinite;
}

.circle-1 {
  width: 80px;
  height: 80px;
  background: var(--pop-red);
  top: 20%;
  left: 10%;
  animation-delay: 0s;
}

.circle-2 {
  width: 120px;
  height: 120px;
  background: var(--pop-cyan);
  top: 60%;
  right: 15%;
  animation-delay: 2s;
}

.circle-3 {
  width: 60px;
  height: 60px;
  background: var(--pop-yellow);
  bottom: 30%;
  left: 20%;
  animation-delay: 4s;
}

.floating-square {
  position: absolute;
  opacity: 0.6;
  animation: rotate 8s linear infinite;
}

.square-1 {
  width: 100px;
  height: 100px;
  background: var(--pop-magenta);
  top: 15%;
  right: 25%;
  animation-delay: 1s;
}

.square-2 {
  width: 70px;
  height: 70px;
  background: var(--pop-green);
  bottom: 20%;
  right: 10%;
  animation-delay: 3s;
}

/* Animations */
@keyframes titleFloat {

  0%,
  100% {
    transform: translateY(0px);
  }

  50% {
    transform: translateY(-10px);
  }
}

@keyframes colorShift {

  0%,
  100% {
    filter: hue-rotate(0deg);
  }

  50% {
    filter: hue-rotate(180deg);
  }
}

@keyframes buttonBounce {

  0%,
  100% {
    transform: translateY(0px);
  }

  50% {
    transform: translateY(-5px);
  }
}

@keyframes float {

  0%,
  100% {
    transform: translateY(0px) rotate(0deg);
  }

  50% {
    transform: translateY(-20px) rotate(180deg);
  }
}

@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}

/* Responsive Design */
@media (max-width: 768px) {
  .main-title {
    font-size: clamp(2rem, 6vw, 4rem);
  }

  .tagline {
    font-size: clamp(1rem, 2.5vw, 1.5rem);
  }

  .cta-button {
    padding: 1rem 2rem;
    font-size: 1rem;
  }

  .floating-circle,
  .floating-square {
    display: none;
  }
}

@media (max-width: 480px) {
  .content {
    padding: 1rem;
  }

  .main-title {
    margin-bottom: 1rem;
  }

  .tagline {
    margin-bottom: 2rem;
  }
}
</style>
