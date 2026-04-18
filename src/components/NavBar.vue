<template>
  <nav :class="['navbar', { scrolled: isScrolled }]">
    <div class="nav-inner">
      <a href="#" class="nav-logo">
        <img src="/images/logo.png" alt="Kape ni Juwana" class="nav-logo-img" />
      </a>
      <ul class="nav-links">
        <li><a href="#about">Story</a></li>
        <li><a href="#menu">Menu</a></li>
        <li><a href="#gallery">Gallery</a></li>
        <li><a href="#location">Visit</a></li>
      </ul>
      <a href="#menu" class="nav-cta">Order Now</a>
      <button class="nav-burger" @click="menuOpen = !menuOpen" aria-label="Menu">
        <span :class="{ open: menuOpen }"></span>
      </button>
    </div>
    <div :class="['mobile-menu', { open: menuOpen }]">
      <a href="#about" @click="menuOpen=false">Story</a>
      <a href="#menu" @click="menuOpen=false">Menu</a>
      <a href="#gallery" @click="menuOpen=false">Gallery</a>
      <a href="#location" @click="menuOpen=false">Visit</a>
      <a href="#menu" @click="menuOpen=false" class="mobile-cta">Order Now</a>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
const isScrolled = ref(false)
const menuOpen = ref(false)
const onScroll = () => { isScrolled.value = window.scrollY > 60 }
onMounted(() => window.addEventListener('scroll', onScroll))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<style scoped>
.navbar {
  position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
  transition: all 0.5s ease;
  padding: 1.4rem 0;
}
.navbar.scrolled {
  background: rgba(26, 14, 7, 0.97);
  backdrop-filter: blur(12px);
  padding: 0.9rem 0;
  box-shadow: 0 2px 40px rgba(0,0,0,0.3);
}
.nav-inner {
  max-width: 1200px; margin: 0 auto;
  padding: 0 2rem;
  display: flex; align-items: center; gap: 2rem;
}
.nav-logo {
  display: flex; align-items: center;
  margin-right: auto;
}
.nav-logo-img {
  height: 64px; width: auto;
  object-fit: contain;
  filter: brightness(0) invert(1);
  transition: filter 0.3s;
}
.nav-links {
  display: flex; list-style: none; gap: 2.5rem;
}
.nav-links a {
  font-family: var(--sans); font-size: 0.78rem; font-weight: 500;
  letter-spacing: 0.15em; text-transform: uppercase;
  color: rgba(245,234,215,0.75);
  transition: color 0.3s;
}
.nav-links a:hover { color: var(--caramel); }
.nav-cta {
  font-family: var(--sans); font-size: 0.72rem; font-weight: 500;
  letter-spacing: 0.15em; text-transform: uppercase;
  color: var(--espresso);
  background: var(--caramel);
  padding: 0.6rem 1.4rem; border-radius: 2px;
  transition: background 0.3s, transform 0.3s;
}
.nav-cta:hover { background: var(--latte); transform: translateY(-1px); }
.nav-burger { display: none; background: none; border: none; cursor: pointer; }
.nav-burger span {
  display: block; width: 22px; height: 1.5px; background: var(--cream);
  position: relative; transition: all 0.3s;
}
.nav-burger span::before, .nav-burger span::after {
  content: ''; position: absolute; width: 22px; height: 1.5px; background: var(--cream);
  transition: all 0.3s;
}
.nav-burger span::before { top: -7px; }
.nav-burger span::after { top: 7px; }
.mobile-menu { display: none; }

@media (max-width: 768px) {
  .nav-links, .nav-cta { display: none; }
  .nav-burger { display: block; }
  .mobile-menu {
    display: flex; flex-direction: column;
    background: var(--espresso);
    max-height: 0; overflow: hidden;
    transition: max-height 0.4s ease;
  }
  .mobile-menu.open { max-height: 400px; }
  .mobile-menu a {
    padding: 1rem 2rem; color: var(--cream);
    font-size: 0.85rem; letter-spacing: 0.1em; text-transform: uppercase;
    border-bottom: 1px solid rgba(255,255,255,0.05);
    transition: color 0.2s;
  }
  .mobile-menu a:hover { color: var(--caramel); }
  .mobile-cta { color: var(--caramel) !important; font-weight: 500; }
}
</style>
