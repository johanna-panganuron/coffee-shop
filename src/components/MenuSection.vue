<template>
  <section class="menu" id="menu">
    <div class="menu-inner">
      <div class="menu-header" data-aos="fade-up">
        <p class="section-label">What We Brew</p>
        <h2 class="section-title">Our <em>signature</em> menu</h2>
      </div>
      <div class="menu-tabs-wrap" data-aos="fade-up" data-aos-delay="100">
  <div class="menu-tabs">
    <button
      v-for="tab in tabs" :key="tab.label"
      :class="['tab-btn', { active: activeTab === tab.label }]"
      @click="activeTab = tab.label"
    >{{ tab.label }} <span class="tab-count">({{ tab.count }})</span></button>
  </div>
</div>
      <div class="menu-grid" data-aos="fade-up" data-aos-delay="150">
        <div class="menu-card" v-for="item in visibleItems" :key="item.name">
          <div class="card-img-wrap">
            <img :src="item.img" :alt="item.name" class="card-img" loading="lazy" />
            <div class="card-overlay">
              <span class="card-tag">{{ item.category }}</span>
            </div>
          </div>
          <div class="card-body">
            <div class="card-top-row">
              <h3 class="card-name">{{ item.name }}</h3>
              <span class="card-price">₱{{ item.price }}</span>
            </div>
            <p class="card-desc">{{ item.desc }}</p>
            <div class="card-notes">
              <span v-for="note in item.notes" :key="note" class="note">{{ note }}</span>
            </div>
          </div>
        </div>
      </div>
      <div class="menu-toggle-wrap" v-if="showToggle">
        <button class="menu-toggle-btn" @click="expanded = !expanded">
          {{ expanded ? 'See Less ↑' : 'See Full Menu ↓' }}
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, watch } from 'vue'

const tabs = computed(() => [
  { label: 'All', count: items.length },
  { label: 'Coffee', count: items.filter(i => i.category === 'Coffee').length },
  { label: 'Tea', count: items.filter(i => i.category === 'Tea').length },
  { label: 'Pastries', count: items.filter(i => i.category === 'Pastries').length },
])

const activeTab = ref('All')
const expanded = ref(false)

const items = [
  // COFFEE (10)
  { name: 'Midnight Espresso', category: 'Coffee', price: 95, desc: 'A straight double shot of rich, dark espresso. Intense, pure, and unapologetic.', notes: ['Bold', 'Dark', 'Pure'], img: '/images/menu/espresso.jpg' },
  { name: 'Slow Brew Americano', category: 'Coffee', price: 115, desc: 'Espresso pulled slow and diluted with hot water for a clean, smooth finish.', notes: ['Smooth', 'Light', 'Classic'], img: '/images/menu/americano.webp' },
  { name: 'Velvet Latte', category: 'Coffee', price: 145, desc: 'Silky steamed milk poured over a double shot for a smooth, comforting everyday cup.', notes: ['Creamy', 'Smooth', 'Warm'], img: '/images/menu/velvet-latte.jpg' },
  { name: 'Cloud Cappuccino', category: 'Coffee', price: 140, desc: 'Equal parts espresso, steamed milk, and thick velvety foam. Light as a cloud.', notes: ['Frothy', 'Bold', 'Classic'], img: '/images/menu/cloud-cappuccino.jpg' },
  { name: 'Golden Caramel Latte', category: 'Coffee', price: 160, desc: 'Espresso and steamed milk finished with a generous drizzle of house-made caramel sauce.', notes: ['Sweet', 'Rich', 'Warm'], img: '/images/menu/golden-caramel-latte.webp' },
  { name: 'Mocha Mood', category: 'Coffee', price: 155, desc: 'Espresso blended with dark chocolate and steamed milk. For the days you need both.', notes: ['Chocolatey', 'Bold', 'Indulgent'], img: '/images/menu/mocha-mood.avif' },
  { name: 'Dulce Spanish Latte', category: 'Coffee', price: 160, desc: 'Espresso with sweetened condensed milk and steamed fresh milk. Rich, sweet, and comforting.', notes: ['Sweet', 'Rich', 'Creamy'], img: '/images/menu/dulce-spanish-latte.jpg' },
  { name: 'Deep Cold Brew', category: 'Coffee', price: 155, desc: 'Steeped for 18 hours in cold water for a naturally sweet, low-acid coffee experience.', notes: ['Smooth', 'Cold', 'Strong'], img: '/images/menu/deep-cold-brew.jpg' },
  { name: 'Iced Velvet Latte', category: 'Coffee', price: 150, desc: 'Espresso over ice with cold milk. Simple, chilled, and satisfying any time of day.', notes: ['Iced', 'Smooth', 'Refreshing'], img: '/images/menu/iced-velvet-latte.webp' },
  { name: 'Chill Americano', category: 'Coffee', price: 120, desc: 'Espresso shots over ice and cold water. Clean, crisp, and endlessly drinkable.', notes: ['Iced', 'Clean', 'Light'], img: '/images/menu/chill-americano.webp' },

  // TEA (7)
  { name: 'Zen Green Tea', category: 'Tea', price: 110, desc: 'Steamed Japanese green tea, clean and grassy with a gentle vegetal sweetness.', notes: ['Earthy', 'Light', 'Calm'], img: '/images/menu/zen-green-tea.jpg' },
  { name: 'Calm Chamomile', category: 'Tea', price: 115, desc: 'Dried chamomile flowers steeped slow for a floral, honey-like calming brew.', notes: ['Floral', 'Calming', 'Warm'], img: '/images/menu/chamomile-tea.jpg' },
  { name: 'Classic Earl Grey', category: 'Tea', price: 115, desc: 'Bold black tea with bergamot oil. Timeless, aromatic, and always reliable.', notes: ['Aromatic', 'Bold', 'Classic'], img: '/images/menu/classic-earl-grey.jpg' },
  { name: 'Honey Glow Tea', category: 'Tea', price: 125, desc: 'Black tea sweetened with raw local honey and a squeeze of calamansi. Warm and glowing.', notes: ['Sweet', 'Citrus', 'Warm'], img: '/images/menu/honey-glow-tea.webp' },
  { name: 'Peach Breeze', category: 'Tea', price: 130, desc: 'Iced black tea infused with ripe peach and a hint of mint. Perfect for warm Cebu afternoons.', notes: ['Fruity', 'Iced', 'Refreshing'], img: '/images/menu/peach-breeze.webp' },
  { name: 'Lychee Bloom', category: 'Tea', price: 135, desc: 'Jasmine green tea with lychee syrup and dried rose petals. Fragrant and lightly sweet.', notes: ['Floral', 'Fruity', 'Delicate'], img: '/images/menu/lychee-bloom.jpg' },
  { name: 'Citrus Calamansi Tea', category: 'Tea', price: 120, desc: 'Fresh calamansi juice steeped with green tea and a touch of muscovado. Proudly local.', notes: ['Citrus', 'Local', 'Bright'], img: '/images/menu/citrus-calamansi-tea.jpg' },

  // PASTRIES (9)
  { name: 'Butter Bliss Croissant', category: 'Pastries', price: 95, desc: 'Classic all-butter croissant, laminated by hand. Shattery outside, pillowy within.', notes: ['Buttery', 'Flaky', 'Classic'], img: '/images/menu/butter-bliss-croissant.webp' },
  { name: 'Choco Dream Croissant', category: 'Pastries', price: 110, desc: 'Butter croissant filled with rich dark chocolate batons. A Parisian staple, done right.', notes: ['Chocolatey', 'Flaky', 'Indulgent'], img: '/images/menu/choco-dream-croissant.jpg' },
  { name: 'Almond Delight Croissant', category: 'Pastries', price: 115, desc: 'Twice-baked croissant filled with almond cream and topped with toasted almond slices.', notes: ['Nutty', 'Sweet', 'Crispy'], img: '/images/menu/almond-delight-croissant.webp' },
  { name: 'Berry Soft Muffin', category: 'Pastries', price: 90, desc: 'Tender muffin bursting with fresh blueberries and a light lemon zest top.', notes: ['Fruity', 'Soft', 'Fresh'], img: '/images/menu/berry-soft-muffin.jpg' },
  { name: 'Dark Cocoa Cake', category: 'Pastries', price: 135, desc: 'Rich layered chocolate cake with dark cocoa ganache. Deep, bittersweet, and satisfying.', notes: ['Rich', 'Dark', 'Decadent'], img: '/images/menu/dark-cocoa-cake.webp' },
  { name: 'Creamy Dream Cheesecake', category: 'Pastries', price: 140, desc: 'New York-style cheesecake with a buttery graham crust. Dense, creamy, and perfectly tangy.', notes: ['Creamy', 'Tangy', 'Rich'], img: '/images/menu/creamy-dream-cheesecake.jpg' },
  { name: 'Fudge Love Brownie', category: 'Pastries', price: 85, desc: 'Dense fudgy brownie with a crinkle top and melted chocolate chunks throughout.', notes: ['Fudgy', 'Chocolatey', 'Dense'], img: '/images/menu/fudge-love-brownie.jpg' },
  { name: 'Cinnamon Swirl', category: 'Pastries', price: 105, desc: 'Soft dough rolled with brown butter cinnamon filling and glazed with cream cheese icing.', notes: ['Spiced', 'Soft', 'Glazed'], img: '/images/menu/cinnamon-swirl.jpg' },
  { name: 'Golden Chip Cookies', category: 'Pastries', price: 80, desc: 'Thick golden cookies with pools of melted chocolate. Crisp edges, chewy center.', notes: ['Chewy', 'Chocolatey', 'Warm'], img: '/images/menu/golden-chip-cookies.jpg' },
]

const filteredItems = computed(() =>
  activeTab.value === 'All' ? items : items.filter(i => i.category === activeTab.value)
)

const visibleItems = computed(() =>
  expanded.value ? filteredItems.value : filteredItems.value.slice(0, 6)
)

const showToggle = computed(() => filteredItems.value.length > 6)

watch(activeTab, () => { expanded.value = false })
</script>

<style scoped>
.menu {
  padding: 8rem 2rem;
  background: var(--parchment);
}

.menu-inner {
  max-width: 1150px;
  margin: 0 auto;
}

.menu-header {
  text-align: center;
  margin-bottom: 2.5rem;
}

.menu-header .section-title {
  color: var(--roast);
}

.menu-tabs-wrap {
  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
  scrollbar-width: none;
  margin-bottom: 3rem;
}
.menu-tabs-wrap::-webkit-scrollbar {
  display: none;
}
.menu-tabs {
  display: flex;
  justify-content: center;
  gap: 0.5rem;
  min-width: max-content;
  padding: 0 1rem;
}
.tab-btn {
  font-family: var(--sans);
  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  padding: 0.55rem 1.4rem;
  border-radius: 2px;
  border: 1px solid var(--cream);
  background: transparent;
  color: var(--text-mid);
  cursor: pointer;
  transition: all 0.3s;
}

.tab-btn:hover {
  border-color: var(--caramel);
  color: var(--caramel);
}

.tab-btn.active {
  background: var(--caramel);
  border-color: var(--caramel);
  color: var(--espresso);
}

.tab-count {
  font-size: 0.65rem;
  opacity: 0.7;
  margin-left: 2px;
}

.menu-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
}

.menu-card {
  background: var(--white);
  border-radius: 2px;
  overflow: hidden;
  transition: transform 0.4s, box-shadow 0.4s;
  border: 1px solid rgba(201, 123, 75, 0.1);
}

.menu-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 20px 50px rgba(44, 26, 14, 0.12);
}

.card-img-wrap {
  position: relative;
  overflow: hidden;
  height: 220px;
}

.card-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s;
}

.menu-card:hover .card-img {
  transform: scale(1.06);
}

.card-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(26, 14, 7, 0.5) 0%, transparent 50%);
  display: flex;
  align-items: flex-end;
  padding: 0.8rem;
}

.card-tag {
  font-size: 0.6rem;
  font-weight: 500;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--caramel);
  background: rgba(26, 14, 7, 0.7);
  padding: 0.25rem 0.6rem;
  border-radius: 2px;
}

.card-body {
  padding: 1.3rem;
}

.card-top-row {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  margin-bottom: 0.5rem;
}

.card-name {
  font-family: var(--serif);
  font-size: 1.15rem;
  font-weight: 600;
  color: var(--roast);
}

.card-price {
  font-family: var(--serif);
  font-size: 1.1rem;
  font-weight: 400;
  color: var(--caramel);
}

.card-desc {
  font-size: 0.8rem;
  color: var(--text-light);
  line-height: 1.7;
  margin-bottom: 0.9rem;
  font-weight: 300;
}

.card-notes {
  display: flex;
  gap: 0.4rem;
  flex-wrap: wrap;
}

.note {
  font-size: 0.6rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  padding: 0.2rem 0.6rem;
  border-radius: 99px;
  border: 1px solid rgba(201, 123, 75, 0.3);
  color: var(--caramel);
}

.menu-toggle-wrap {
  display: flex;
  justify-content: center;
  margin-top: 3rem;
}

.menu-toggle-btn {
  font-family: var(--sans);
  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  padding: 0.75rem 2.5rem;
  border: 1px solid var(--caramel);
  background: transparent;
  color: var(--caramel);
  border-radius: 2px;
  cursor: pointer;
  transition: all 0.3s;
}

.menu-toggle-btn:hover {
  background: var(--caramel);
  color: var(--espresso);
}

@media (max-width: 900px) {
  .menu-grid {
    grid-template-columns: 1fr 1fr;
  }
}

@media (max-width: 560px) {
  .menu-grid {
    grid-template-columns: 1fr;
  }
  .menu-tabs {
    justify-content: flex-start;
  }
  .tab-btn {
    white-space: nowrap;
    padding: 0.5rem 1rem;
    font-size: 0.7rem;
  }
}
</style>
