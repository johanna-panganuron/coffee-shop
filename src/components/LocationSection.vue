<template>
  <section class="location" id="location">
    <div class="location-inner">
      <div class="location-info" data-aos="fade-right">
        <p class="section-label">Find Us</p>
        <h2 class="section-title">Come <em>visit</em></h2>
        <div class="info-blocks">
          <div class="info-block">
            <span class="info-icon">o</span>
            <div>
              <strong>Address</strong>
              <p>1 Catarman Rd, Cordova, Cebu</p>
            </div>
          </div>
          <div class="info-block">
            <span class="info-icon">o</span>
            <div>
              <strong>Hours</strong>
              <div class="hours-grid">
                <span>Mon – Fri</span><span>7:00 AM – 9:00 PM</span>
                <span>Saturday</span><span>8:00 AM – 10:00 PM</span>
                <span>Sunday</span><span>8:00 AM – 8:00 PM</span>
              </div>
            </div>
          </div>
          <div class="info-block">
            <span class="info-icon">o</span>
            <div>
              <strong>Contact</strong>
              <p>hello@kapenijuwana.ph<br/>+63 949 128 0100</p>
            </div>
          </div>
        </div>
        <div class="socials">
          <a href="#" class="social-link">Instagram</a>
          <a href="#" class="social-link">Facebook</a>
          <a href="#" class="social-link">TikTok</a>
        </div>
      </div>
      <div class="location-map" data-aos="fade-left" data-aos-delay="100">
        <iframe
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3924.9!2d123.9571!3d10.2573!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x33a99b1c2f5b5b5b%3A0x0!2sCatarman+Rd%2C+Cordova%2C+Cebu!5e0!3m2!1sen!2sph!4v1234567890"
          width="100%" height="100%" style="border:0;" allowfullscreen="" loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"
          title="Kape ni Juwana location"
        ></iframe>
        <div class="map-label">1 Catarman Rd, Cordova, Cebu</div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.location { padding: 8rem 2rem; background: var(--parchment); }
.location-inner {
  max-width: 1100px; margin: 0 auto;
  display: grid; grid-template-columns: 1fr 1.1fr;
  gap: 5rem; align-items: start;
}
.location-info .section-title { color: var(--roast); margin-bottom: 2.5rem; }
.info-blocks { display: flex; flex-direction: column; gap: 1.8rem; margin-bottom: 2.5rem; }
.info-block { display: flex; gap: 1rem; align-items: flex-start; }
.info-icon { color: var(--caramel); font-size: 1rem; margin-top: 0.15rem; flex-shrink: 0; }
.info-block strong {
  display: block; font-size: 0.72rem; font-weight: 500;
  letter-spacing: 0.12em; text-transform: uppercase;
  color: var(--caramel); margin-bottom: 0.4rem;
}
.info-block p { font-size: 0.9rem; color: var(--text-mid); line-height: 1.8; font-weight: 300; }
.hours-grid {
  display: grid; grid-template-columns: auto 1fr;
  gap: 0.2rem 1.5rem;
  font-size: 0.85rem; color: var(--text-mid); font-weight: 300;
}
.socials { display: flex; gap: 1.5rem; }
.social-link {
  font-size: 0.72rem; font-weight: 500; letter-spacing: 0.12em; text-transform: uppercase;
  color: var(--text-light);
  border-bottom: 1px solid transparent;
  padding-bottom: 1px;
  transition: color 0.3s, border-color 0.3s;
}
.social-link:hover { color: var(--caramel); border-color: var(--caramel); }

.location-map {
  position: relative;
  height: 460px; border-radius: 2px; overflow: hidden;
  border: 1px solid rgba(201,123,75,0.15);
}
.location-map iframe { filter: sepia(30%) contrast(0.9); height: calc(100% - 40px); }
.map-label {
  position: absolute; bottom: 0; left: 0; right: 0;
  background: var(--caramel); color: var(--espresso);
  font-size: 0.72rem; font-weight: 500; letter-spacing: 0.1em;
  text-align: center; padding: 0.6rem;
  height: 40px; display: flex; align-items: center; justify-content: center;
}

@media (max-width: 860px) {
  .location-inner { grid-template-columns: 1fr; gap: 3rem; }
  .location-map { height: 320px; }
}
</style>
