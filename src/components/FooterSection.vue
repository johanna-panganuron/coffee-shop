<template>
  <footer class="footer">
    <div class="footer-top">
      <div class="footer-brand">
        <div class="footer-logo">
          <img src="/images/logo.png" alt="Kape ni Juwana" class="footer-logo-img" />
        </div>
        <p class="footer-tagline">Specialty coffee from the<br/>heart of Cordova, Cebu.</p>
        <form class="newsletter" @submit.prevent>
          <input type="email" placeholder="Your email address" class="nl-input" />
          <button type="submit" class="nl-btn">Subscribe</button>
        </form>
      </div>
      <div class="footer-nav">
        <div class="footer-col">
          <h4>Navigate</h4>
          <a href="#about">Our Story</a>
          <a href="#menu">Menu</a>
          <a href="#gallery">Gallery</a>
          <a href="#location">Visit Us</a>
        </div>
        <div class="footer-col">
          <h4>Follow</h4>
          <a href="#">Instagram</a>
          <a href="#">Facebook</a>
          <a href="#">TikTok</a>
        </div>
        <div class="footer-col">
          <h4>Info</h4>
          <a href="#">Careers</a>
          <a href="#">Wholesale</a>
          <a href="#">Press</a>
          <a href="#">FAQs</a>
        </div>
      </div>
    </div>
    <div class="footer-bottom">
      <p>© {{ year }} Kape ni Juwana. All rights reserved.</p>
      <p class="footer-credit">
  Crafted with 
  <span class="footer-coffee-icon" v-html="`<svg width='14' height='14' viewBox='0 0 24 24' fill='none' stroke='currentColor' stroke-width='1.5' stroke-linecap='round'><path d='M6 2c0 0 1 2 0 4'/><path d='M12 2c0 0 1 2 0 4'/><path d='M3 8h14l-2 10H5L3 8z'/><path d='M17 10h2a2 2 0 0 1 0 4h-2'/></svg>`"></span>
  in Cordova, Cebu
</p>
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()
</script>

<style scoped>
.footer { background: var(--espresso); color: rgba(245,234,215,0.6); }
.footer-top {
  max-width: 1100px; margin: 0 auto;
  padding: 5rem 2rem 3rem;
  display: grid; grid-template-columns: 1.5fr 1fr;
  gap: 4rem;
}
.footer-logo { margin-bottom: 1rem; }
.footer-logo-img {
  height: 64px; width: auto;
  object-fit: contain;
  mix-blend-mode: screen;
}
.footer-tagline { font-size: 0.85rem; line-height: 1.8; margin-bottom: 2rem; font-weight: 300; }
.newsletter { display: flex; gap: 0; max-width: 340px; }
.nl-input {
  flex: 1; padding: 0.7rem 1rem;
  background: rgba(255,255,255,0.06); border: 1px solid rgba(255,255,255,0.1);
  border-right: none; border-radius: 2px 0 0 2px;
  color: var(--cream); font-family: var(--sans); font-size: 0.8rem;
  outline: none;
}
.nl-input::placeholder { color: rgba(245,234,215,0.3); }
.nl-btn {
  padding: 0.7rem 1.2rem; background: var(--caramel); color: var(--espresso);
  border: none; border-radius: 0 2px 2px 0;
  font-family: var(--sans); font-size: 0.72rem; font-weight: 500;
  letter-spacing: 0.1em; text-transform: uppercase;
  cursor: pointer; transition: background 0.3s;
}
.nl-btn:hover { background: var(--latte); }
.footer-nav { display: flex; gap: 3rem; }
.footer-col { display: flex; flex-direction: column; gap: 0.7rem; }
.footer-col h4 {
  font-size: 0.65rem; font-weight: 500; letter-spacing: 0.2em; text-transform: uppercase;
  color: var(--caramel); margin-bottom: 0.3rem;
}
.footer-col a {
  font-size: 0.82rem; color: rgba(245,234,215,0.5);
  transition: color 0.2s; font-weight: 300;
}
.footer-col a:hover { color: var(--cream); }
.footer-bottom {
  max-width: 1100px; margin: 0 auto;
  padding: 1.5rem 2rem;
  border-top: 1px solid rgba(255,255,255,0.06);
  display: flex; justify-content: space-between; align-items: center;
  font-size: 0.72rem;
}
.footer-credit { color: rgba(245,234,215,0.3); }
.footer-coffee-icon {
  display: inline-flex;
  align-items: center;
  vertical-align: middle;
  color: var(--caramel);
  margin: 0 2px;
  position: relative;
  top: -1px;
}
@media (max-width: 768px) {
  .footer-top { grid-template-columns: 1fr; gap: 2.5rem; }
  .footer-bottom { flex-direction: column; gap: 0.5rem; text-align: center; }
}
</style>