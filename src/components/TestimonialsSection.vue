<template>
  <section class="testimonials">
    <div class="test-inner">
      <div class="test-header" data-aos="fade-up">
        <p class="section-label">What people say</p>
        <h2 class="section-title">Loved by <em>regulars</em></h2>
      </div>
      <div class="test-track-wrap" data-aos="fade-up" data-aos-delay="100">
        <div class="test-track" :style="{ transform: `translateX(-${activeIndex * 100}%)` }">
          <div class="test-card" v-for="t in testimonials" :key="t.name">
            <div class="stars">★★★★★</div>
            <blockquote class="test-quote">"{{ t.quote }}"</blockquote>
            <div class="test-author">
              <div class="author-avatar">{{ t.name[0] }}</div>
              <div>
                <strong>{{ t.name }}</strong>
                <span>{{ t.title }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="test-dots">
        <button
          v-for="(_, i) in testimonials" :key="i"
          :class="['dot', { active: i === activeIndex }]"
          @click="activeIndex = i"
          :aria-label="`Review ${i+1}`"
        ></button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const activeIndex = ref(0)
let timer

const testimonials = [
  { name: 'Catherine Inoc', title: 'Graphic Designer', quote: 'I come here every morning without fail. The Sagada Pour Over is unlike anything else in the city — it genuinely changed how I think about coffee.' },
  { name: 'Stacey Sevilleja', title: 'Freelance Writer', quote: 'The kind of café where you sit down for 20 minutes and end up staying 3 hours. Warm, unhurried, and the Cold Brew Tonic is dangerously good.' },
  { name: 'Jhoanna Robles', title: 'Architecture Student', quote: 'Brûlé feels handmade in the best possible way. Every detail, from the cups to the playlists, is thoughtful. My favorite spot to work in QC.' },
  { name: 'Stellvester Ajero', title: 'Software Engineer', quote: 'I\'ve tried every specialty café in the Metro. None of them have the character of Brûlé. The Kouign-Amann pairs perfectly with literally anything.' },
]

onMounted(() => {
  timer = setInterval(() => {
    activeIndex.value = (activeIndex.value + 1) % testimonials.length
  }, 5000)
})
onUnmounted(() => clearInterval(timer))
</script>

<style scoped>
.testimonials { padding: 8rem 2rem; background: var(--bark); }
.test-inner { max-width: 800px; margin: 0 auto; }
.test-header { text-align: center; margin-bottom: 3rem; }
.test-header .section-title { color: var(--cream); }
.test-header .section-label { color: var(--caramel); }

.test-track-wrap { overflow: hidden; border-radius: 2px; }
.test-track {
  display: flex; transition: transform 0.6s cubic-bezier(0.25,0.8,0.25,1);
}
.test-card {
  min-width: 100%; padding: 3rem;
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(255,255,255,0.07);
  border-radius: 2px;
}
.stars { color: var(--caramel); font-size: 1rem; margin-bottom: 1.5rem; letter-spacing: 0.1em; }
.test-quote {
  font-family: var(--serif); font-size: clamp(1.1rem, 2.5vw, 1.4rem);
  font-style: italic; font-weight: 300; line-height: 1.65;
  color: var(--cream); margin-bottom: 2rem;
}
.test-author { display: flex; align-items: center; gap: 1rem; }
.author-avatar {
  width: 44px; height: 44px; border-radius: 50%;
  background: var(--caramel); color: var(--espresso);
  font-family: var(--serif); font-size: 1.2rem; font-weight: 600;
  display: flex; align-items: center; justify-content: center;
  flex-shrink: 0;
}
.test-author strong {
  display: block; font-size: 0.9rem; font-weight: 500; color: var(--cream);
}
.test-author span { font-size: 0.75rem; color: rgba(245,234,215,0.45); }

.test-dots { display: flex; justify-content: center; gap: 0.5rem; margin-top: 2rem; }
.dot {
  width: 6px; height: 6px; border-radius: 50%;
  background: rgba(245,234,215,0.2); border: none; cursor: pointer;
  transition: background 0.3s, transform 0.3s;
}
.dot.active { background: var(--caramel); transform: scale(1.4); }
</style>
