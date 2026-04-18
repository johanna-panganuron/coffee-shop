<template>
  <section class="about" id="about">
    <div class="about-inner">
      <div class="about-image-wrap" data-aos="fade-right">
        <img src="https://images.unsplash.com/photo-1501339847302-ac426a4a7cbb?w=800&auto=format&fit=crop"
          alt="Barista crafting coffee" class="about-img" />
        <div class="about-img-accent"></div>
        <div class="about-stat">
          <span class="stat-num">5+</span>
          <span class="stat-label">Years of craft</span>
        </div>
      </div>
      <div class="about-text" data-aos="fade-left" data-aos-delay="100">
        <p class="section-label">Our Story</p>
        <h2 class="section-title">Brewed from<br /><em>passion</em>, not pressure.</h2>
        <p class="about-desc">
          Kape ni Juwana began in 2019 as a tiny corner stall in Cordova, Cebu -- just a hand grinder, a kettle, and a
          stubborn belief that coffee could be something more than a morning routine.
        </p>
        <p class="about-desc">
          We source single-origin beans directly from the highlands of Tuburan and Alcoy,
          roasted in small batches to honor every note -- the fruit, the earth, the smoke.
        </p>
        <div class="about-pillars">
          <div class="pillar" v-for="p in pillars" :key="p.label">
            <span class="pillar-icon">{{ p.icon }}</span>
            <div>
              <strong>{{ p.label }}</strong>
              <p>{{ p.text }}</p>
            </div>
          </div>
        </div>
        <a href="#menu" class="about-link">See what we're brewing →</a>
      </div>
    </div>
  </section>
</template>

<script setup>
const pillars = [
  { icon: 'o', label: 'Single Origin', text: 'Direct from Philippine highland farms.' },
  { icon: 'o', label: 'Small Batch Roast', text: 'Roasted weekly, never stockpiled.' },
  { icon: 'o', label: 'No Rush Culture', text: 'Slow coffee for slow mornings.' },
]
</script>

<style scoped>
.about {
  padding: 8rem 2rem;
  background: var(--roast);
}

.about-inner {
  max-width: 1100px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 6rem;
  align-items: center;
}

.about-image-wrap {
  position: relative;
}

.about-img {
  width: 100%;
  height: 560px;
  object-fit: cover;
  border-radius: 2px;
  filter: sepia(20%) contrast(1.05);
}

.about-img-accent {
  position: absolute;
  bottom: -20px;
  right: -20px;
  width: 60%;
  height: 60%;
  border: 2px solid var(--caramel);
  border-radius: 2px;
  z-index: -1;
  opacity: 0.4;
}

.about-stat {
  position: absolute;
  top: 2rem;
  left: -2rem;
  background: var(--caramel);
  color: var(--espresso);
  padding: 1.2rem 1.5rem;
  text-align: center;
  border-radius: 2px;
}

.stat-num {
  display: block;
  font-family: var(--serif);
  font-size: 2.5rem;
  font-weight: 600;
  line-height: 1;
}

.stat-label {
  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.about-text .section-title {
  color: var(--cream);
  margin-bottom: 1.5rem;
}

.about-text .section-label {
  color: var(--caramel);
}

.about-desc {
  font-size: 0.95rem;
  color: rgba(245, 234, 215, 0.7);
  margin-bottom: 1.2rem;
  font-weight: 300;
}

.about-pillars {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin: 2rem 0;
}

.pillar {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
}

.pillar-icon {
  color: var(--caramel);
  font-size: 1rem;
  margin-top: 0.15rem;
  flex-shrink: 0;
}

.pillar strong {
  display: block;
  font-size: 0.85rem;
  font-weight: 500;
  color: var(--cream);
  letter-spacing: 0.05em;
  margin-bottom: 0.1rem;
}

.pillar p {
  font-size: 0.8rem;
  color: rgba(245, 234, 215, 0.55);
  font-weight: 300;
}

.about-link {
  font-family: var(--sans);
  font-size: 0.8rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  color: var(--caramel);
  border-bottom: 1px solid rgba(201, 123, 75, 0.4);
  padding-bottom: 2px;
  transition: border-color 0.3s, letter-spacing 0.3s;
  display: inline-block;
}

.about-link:hover {
  border-color: var(--caramel);
  letter-spacing: 0.15em;
}

@media (max-width: 860px) {
  .about-inner {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .about-stat {
    left: 1rem;
  }

  .about-img {
    height: 350px;
  }
}</style>
