<template>
  <div id="app">
    <NavBar />
    <HeroSection />
    <AboutSection />
    <MenuSection />
    <FeaturesSection />
    <GallerySection />
    <TestimonialsSection />
    <LocationSection />
    <FooterSection />
  </div>
</template>

<script setup>
import { onMounted } from 'vue'
import AOS from 'aos'
import 'aos/dist/aos.css'

import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import MenuSection from './components/MenuSection.vue'
import FeaturesSection from './components/FeaturesSection.vue'
import GallerySection from './components/GallerySection.vue'
import TestimonialsSection from './components/TestimonialsSection.vue'
import LocationSection from './components/LocationSection.vue'
import FooterSection from './components/FooterSection.vue'

onMounted(() => {
  AOS.init({ duration: 800, easing: 'ease-out-cubic', once: true, offset: 80 })
})
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;0,700;1,300;1,400&family=Jost:wght@300;400;500&display=swap');

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --espresso: #1a0e07;
  --roast: #2c1a0e;
  --bark: #4a2c1a;
  --caramel: #c97b4b;
  --latte: #d4a574;
  --cream: #f5ead7;
  --parchment: #faf4eb;
  --white: #fff9f3;
  --text-dark: #1a0e07;
  --text-mid: #5c3d2e;
  --text-light: #9c7b6a;
  --serif: 'Cormorant Garamond', Georgia, serif;
  --sans: 'Jost', sans-serif;
  --transition: 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
}

html { scroll-behavior: smooth; }

body {
  font-family: var(--sans);
  background: var(--parchment);
  color: var(--text-dark);
  line-height: 1.7;
  overflow-x: hidden;
}

img { max-width: 100%; display: block; }
a { text-decoration: none; color: inherit; }
section { overflow: hidden; }

.section-label {
  font-family: var(--sans);
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: var(--caramel);
  margin-bottom: 0.75rem;
}

.section-title {
  font-family: var(--serif);
  font-size: clamp(2.2rem, 5vw, 3.5rem);
  font-weight: 300;
  line-height: 1.15;
  color: var(--roast);
}

.section-title em {
  font-style: italic;
  color: var(--caramel);
}

::-webkit-scrollbar { width: 6px; }
::-webkit-scrollbar-track { background: var(--cream); }
::-webkit-scrollbar-thumb { background: var(--caramel); border-radius: 3px; }
</style>
