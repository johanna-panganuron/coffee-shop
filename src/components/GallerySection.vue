<template>
  <section class="gallery" id="gallery">
    <div class="gallery-header" data-aos="fade-up">
      <p class="section-label">Moments</p>
      <h2 class="section-title">A taste of <em> Kape ni Juwana</em></h2>
    </div>
    <div class="gallery-grid">
      <div
        class="gallery-item"
        v-for="(img, i) in images" :key="i"
        :class="img.size"
        data-aos="fade-up"
        :data-aos-delay="i * 60"
        @click="openLightbox(i)"
      >
        <img :src="img.src" :alt="img.alt" loading="lazy" />
        <div class="gallery-hover">
          <span>+</span>
        </div>
      </div>
    </div>
    <Teleport to="body">
      <div class="lightbox" v-if="lightboxIndex !== null" @click.self="closeLightbox">
        <button class="lb-close" @click="closeLightbox">✕</button>
        <button class="lb-prev" @click="prev">‹</button>
        <img :src="images[lightboxIndex].src" :alt="images[lightboxIndex].alt" class="lb-img" />
        <button class="lb-next" @click="next">›</button>
      </div>
    </Teleport>
  </section>
</template>

<script setup>
import { ref } from 'vue'
const lightboxIndex = ref(null)
const openLightbox = (i) => { lightboxIndex.value = i }
const closeLightbox = () => { lightboxIndex.value = null }
const prev = () => { lightboxIndex.value = (lightboxIndex.value - 1 + images.length) % images.length }
const next = () => { lightboxIndex.value = (lightboxIndex.value + 1) % images.length }

const images = [
  { src: 'https://images.unsplash.com/photo-1442512595331-e89e73853f31?w=700&auto=format&fit=crop', alt: 'Latte art', size: 'tall' },
  { src: 'https://images.unsplash.com/photo-1509042239860-f550ce710b93?w=600&auto=format&fit=crop', alt: 'Espresso shot', size: '' },
  { src: 'https://images.unsplash.com/photo-1554118811-1e0d58224f24?w=600&auto=format&fit=crop', alt: 'Cafe interior', size: '' },
  { src: 'https://images.unsplash.com/photo-1498804103079-a6351b050096?w=700&auto=format&fit=crop', alt: 'Coffee beans', size: 'wide' },
  { src: 'https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=600&auto=format&fit=crop', alt: 'Pour over brew', size: '' },
  { src: 'https://images.unsplash.com/photo-1541167760496-1628856ab772?w=600&auto=format&fit=crop', alt: 'Coffee and pastry', size: '' },
  { src: 'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=600&auto=format&fit=crop', alt: 'Iced coffee', size: '' },
]
</script>

<style scoped>
.gallery { padding: 8rem 2rem; background: var(--cream); }
.gallery-header { text-align: center; margin-bottom: 3rem; }
.gallery-header .section-title { color: var(--roast); }
.gallery-grid {
  max-width: 1150px; margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: auto;
  gap: 1rem;
}
.gallery-item {
  position: relative; overflow: hidden;
  border-radius: 2px; cursor: pointer;
  height: 260px;
}
.gallery-item.tall { grid-row: span 2; height: auto; min-height: 380px; }
.gallery-item.wide { grid-column: span 2; }
.gallery-item img {
  width: 100%; height: 100%; object-fit: cover;
  transition: transform 0.6s cubic-bezier(0.25,0.8,0.25,1);
  filter: sepia(10%);
}
.gallery-item:hover img { transform: scale(1.07); filter: sepia(0%); }
.gallery-hover {
  position: absolute; inset: 0;
  background: rgba(26,14,7,0.45);
  display: flex; align-items: center; justify-content: center;
  opacity: 0; transition: opacity 0.3s;
  color: var(--cream); font-size: 2rem;
}
.gallery-item:hover .gallery-hover { opacity: 1; }

.lightbox {
  position: fixed; inset: 0; z-index: 9999;
  background: rgba(10,5,2,0.95);
  display: flex; align-items: center; justify-content: center;
  animation: fadeIn 0.3s ease;
}
@keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
.lb-img {
  max-width: 90vw; max-height: 85vh; object-fit: contain;
  border-radius: 2px;
}
.lb-close {
  position: absolute; top: 1.5rem; right: 1.5rem;
  background: none; border: none; color: var(--cream);
  font-size: 1.2rem; cursor: pointer; opacity: 0.7; transition: opacity 0.2s;
}
.lb-close:hover { opacity: 1; }
.lb-prev, .lb-next {
  position: absolute; top: 50%; transform: translateY(-50%);
  background: none; border: none; color: var(--cream);
  font-size: 3rem; cursor: pointer; opacity: 0.5; transition: opacity 0.2s;
  padding: 1rem;
}
.lb-prev:hover, .lb-next:hover { opacity: 1; }
.lb-prev { left: 1rem; }
.lb-next { right: 1rem; }

@media (max-width: 700px) {
  .gallery-grid { grid-template-columns: 1fr 1fr; }
  .gallery-item.tall { grid-row: span 1; min-height: 200px; }
  .gallery-item.wide { grid-column: span 1; }
}
@media (max-width: 440px) {
  .gallery-grid { grid-template-columns: 1fr; }
}
</style>
