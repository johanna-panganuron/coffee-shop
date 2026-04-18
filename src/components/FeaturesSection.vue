<template>
  <section class="features">
    <div class="features-inner">
      <div
        class="feature"
        v-for="(f, i) in features"
        :key="f.label"
        data-aos="fade-up"
        :data-aos-delay="i * 100"
      >
        <div class="feature-icon" v-html="f.svg"></div>
        <h3 class="feature-label">{{ f.label }}</h3>
        <p class="feature-text">{{ f.text }}</p>
      </div>
    </div>
  </section>
</template>

<script setup>
const bean = `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"><ellipse cx="12" cy="12" rx="8" ry="5" transform="rotate(-35 12 12)"/><path d="M12 12 Q9 8 12 4"/></svg>`
const cup = `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"><path d="M6 2c0 0 1 2 0 4"/><path d="M12 2c0 0 1 2 0 4"/><path d="M3 8h14l-2 10H5L3 8z"/><path d="M17 10h2a2 2 0 0 1 0 4h-2"/></svg>`
const leaf = `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"><path d="M12 22C12 22 4 16 4 9a8 8 0 0 1 16 0c0 7-8 13-8 13z"/><path d="M12 9v13"/></svg>`
const star = `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"><path d="M12 2l2.4 7.4H22l-6.2 4.5 2.4 7.4L12 17l-6.2 4.3 2.4-7.4L2 9.4h7.6z"/></svg>`

const features = [
  { svg: bean, label: 'Locally Sourced Beans', text: 'We partner directly with small highland farms of Tuburan and Alcoy, ensuring fair pay and exceptional quality.' },
  { svg: cup, label: 'Handcrafted Daily', text: "Every cup is pulled to order. No batch brewing, no shortcuts -- just patient hands and precise technique." },
  { svg: leaf, label: 'A Cozy Corner', text: "Designed to feel like your living room. Stay an hour or all day -- we're not rushing anyone out." },
  { svg: star, label: 'Seasonal Specials', text: "Our menu rotates with the harvest. When Benguet strawberries arrive, you'll know about it." },
]
</script>

<style scoped>
.features {
  background: var(--espresso);
  padding: 6rem 2rem;
}
.features-inner {
  max-width: 1100px; margin: 0 auto;
  display: grid; grid-template-columns: repeat(4, 1fr);
  gap: 2.5rem;
}
.feature {
  text-align: center; padding: 1.5rem 1rem;
  border-right: 1px solid rgba(255,255,255,0.06);
  transition: transform 0.3s;
}
.feature:hover { transform: translateY(-4px); }
.feature:last-child { border-right: none; }
.feature-icon {
  color: var(--caramel);
  margin-bottom: 1.2rem;
  display: flex; justify-content: center;
}
.feature-label {
  font-family: var(--serif); font-size: 1.15rem; font-weight: 600;
  color: var(--cream); margin-bottom: 0.75rem;
}
.feature-text {
  font-size: 0.8rem; color: rgba(245,234,215,0.5);
  line-height: 1.8; font-weight: 300;
}
@media (max-width: 860px) {
  .features-inner { grid-template-columns: 1fr 1fr; }
  .feature { border-right: none; border-bottom: 1px solid rgba(255,255,255,0.06); padding: 2rem 1rem; }
  .feature:nth-last-child(-n+2) { border-bottom: none; }
}
@media (max-width: 480px) {
  .features-inner { grid-template-columns: 1fr; }
  .feature { border-bottom: 1px solid rgba(255,255,255,0.06); }
  .feature:last-child { border-bottom: none; }
}
</style>
