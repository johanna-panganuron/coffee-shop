<template>
  <section class="hero" id="home">
    <div class="hero-bg">
      <img
        src="https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=1800&auto=format&fit=crop"
        alt="Coffee shop atmosphere"
        class="hero-img"
      />
      <div class="hero-overlay"></div>
    </div>
    <div class="hero-content">
      <p class="hero-eyebrow">Est. 2019 — Cordova, Cebu</p>
      <h1 class="hero-title">
        Where every<br/>
        <em>cup</em> tells<br/>
        a story.
      </h1>
      <p class="hero-sub">Specialty coffee, slow mornings, and a warm corner<br/>to call your own.</p>
      <div class="hero-actions">
        <a href="#menu" class="btn-primary">Explore the Menu</a>
        <a href="#about" class="btn-ghost">Our Story ↓</a>
      </div>
    </div>
    <div class="hero-scroll" @click="scrollDown">
      <span class="scroll-line"></span>
      <span class="scroll-text">Scroll</span>
    </div>
    <!-- <div class="hero-badge">
      <div class="badge-ring">
        <span>Single Origin · Handcrafted · Daily Fresh ·&nbsp;</span>
        <span>Single Origin · Handcrafted · Daily Fresh ·&nbsp;</span>
      </div>
      <div class="badge-center">✦</div>
    </div> -->
  </section>
</template>

<script setup>
const scrollDown = () => {
  document.getElementById('about').scrollIntoView({ behavior: 'smooth' })
}
</script>

<style scoped>
.hero {
  position: relative; height: 100dvh; min-height: 600px;
  display: flex; align-items: center; justify-content: center;
  overflow: hidden;
}
.hero-bg {
  position: absolute; inset: 0;
}
.hero-img {
  width: 100%; height: 100%; object-fit: cover;
  animation: kenburns 18s ease-in-out infinite alternate;
}
@keyframes kenburns {
  from { transform: scale(1) translate(0, 0); }
  to   { transform: scale(1.08) translate(-1%, 1%); }
}
.hero-overlay {
  position: absolute; inset: 0;
  background: linear-gradient(
    160deg,
    rgba(26,14,7,0.75) 0%,
    rgba(26,14,7,0.5) 50%,
    rgba(26,14,7,0.72) 100%
  );
}
.hero-content {
  position: relative; z-index: 2;
  text-align: center; padding: 2rem;
  max-width: 800px;
  animation: fadeUp 1.2s 0.3s both;
}
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(30px); }
  to   { opacity: 1; transform: translateY(0); }
}
.hero-eyebrow {
  font-family: var(--sans); font-size: 0.7rem; font-weight: 400;
  letter-spacing: 0.3em; text-transform: uppercase;
  color: var(--caramel); margin-bottom: 1.5rem;
}
.hero-title {
  font-family: var(--serif);
  font-size: clamp(3.5rem, 10vw, 7.5rem);
  font-weight: 300; line-height: 1.05;
  color: var(--cream);
  margin-bottom: 1.5rem;
}
.hero-title em {
  font-style: italic; color: var(--caramel);
}
.hero-sub {
  font-family: var(--sans); font-size: 1rem; font-weight: 300;
  color: rgba(245,234,215,0.7); line-height: 1.8;
  margin-bottom: 2.5rem;
}
.hero-actions { display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; }
.btn-primary {
  font-family: var(--sans); font-size: 0.75rem; font-weight: 500;
  letter-spacing: 0.15em; text-transform: uppercase;
  background: var(--caramel); color: var(--espresso);
  padding: 0.9rem 2.2rem; border-radius: 2px;
  transition: all 0.3s;
}
.btn-primary:hover { background: var(--latte); transform: translateY(-2px); box-shadow: 0 8px 30px rgba(201,123,75,0.4); }
.btn-ghost {
  font-family: var(--sans); font-size: 0.75rem; font-weight: 400;
  letter-spacing: 0.1em;
  color: rgba(245,234,215,0.8);
  padding: 0.9rem 1.5rem;
  border: 1px solid rgba(245,234,215,0.25); border-radius: 2px;
  transition: all 0.3s;
}
.btn-ghost:hover { border-color: var(--caramel); color: var(--caramel); }

.hero-scroll {
  position: absolute; bottom: 2.5rem; left: 50%; transform: translateX(-50%);
  z-index: 2; display: flex; flex-direction: column; align-items: center; gap: 0.5rem;
  cursor: pointer; color: rgba(245,234,215,0.5);
}
.scroll-line {
  display: block; width: 1px; height: 50px;
  background: linear-gradient(to bottom, transparent, var(--caramel));
  animation: scrollPulse 2s ease-in-out infinite;
}
@keyframes scrollPulse {
  0%, 100% { opacity: 0.3; transform: scaleY(0.7); }
  50% { opacity: 1; transform: scaleY(1); }
}
.scroll-text { font-size: 0.6rem; letter-spacing: 0.2em; text-transform: uppercase; }

.hero-badge {
  position: absolute; bottom: 2rem; right: 2.5rem; z-index: 2;
  width: 90px; height: 90px;
  display: flex; align-items: center; justify-content: center;
}
.badge-ring {
  position: absolute; inset: 0;
  font-size: 0.38rem; letter-spacing: 0.12em; text-transform: uppercase;
  color: rgba(245,234,215,0.4);
  animation: spin 20s linear infinite;
  display: flex; align-items: center; justify-content: center;
  white-space: nowrap; overflow: hidden; border-radius: 50%;
}
@keyframes spin { to { transform: rotate(360deg); } }
.badge-center {
  font-size: 1.1rem; color: var(--caramel); z-index: 1;
}

@media (max-width: 600px) {
  .hero-badge { display: none; }
}
</style>
