<template>
  <section id="actualites" class="news">
    <div class="news-container">
      <h2 class="news-title">Actualité</h2>

      <div class="news-carousel-wrapper">
        <button class="nav-arrow nav-arrow-left" @click="prevSlide" :disabled="currentSlide === 0">
          <ChevronLeftIcon class="arrow-icon" />
        </button>

        <div
          class="news-carousel"
          @touchstart="handleTouchStart"
          @touchmove="handleTouchMove"
          @touchend="handleTouchEnd"
        >
          <div class="news-track" :style="trackTransform">
            <article class="news-card">
              <div class="news-image">
                <img src="@/assets/blog/blog1.webp" alt="Salon King of Hair" />
              </div>
              <div class="news-content">
                <h3 class="news-card-title">Ouverture du salon en juillet 2026</h3>
                <p class="news-text">
                  Nous sommes ravis de vous annoncer l'ouverture prochaine de King of Hair à Chambéry !
                  Après plusieurs mois de préparation et d'aménagement, notre salon de coiffure pour hommes
                  ouvrira ses portes en juillet 2026.
                </p>
                <p class="news-text">
                  Situé au cœur de Chambéry, King of Hair vous proposera des prestations de qualité dans
                  un cadre moderne et élégant. Que ce soit pour une coupe classique, un rasage traditionnel,
                  une taille de barbe ou un soin du visage, notre équipe de professionnels passionnés sera
                  à votre écoute pour vous offrir un service personnalisé.
                </p>
                <p class="news-text">
                  Nous mettons tout en œuvre pour créer un espace où tradition et modernité se rencontrent,
                  où chaque client bénéficie d'une expérience unique dans une ambiance conviviale et raffinée.
                  Restez connectés pour découvrir bientôt plus de détails sur nos services, nos horaires et
                  nos offres de lancement !
                </p>
              </div>
            </article>

            <article class="news-card">
              <div class="news-image">
                <img src="@/assets/blog/blog2.png" alt="Prise de rendez-vous" />
              </div>
              <div class="news-content">
                <h3 class="news-card-title">Prise de rendez-vous</h3>
                <p class="news-text">
                  Pour vous garantir un service de qualité et personnalisé, toutes nos prestations seront
                  effectuées uniquement sur rendez-vous. Cette approche nous permet de consacrer à chaque
                  client le temps et l'attention qu'il mérite, sans attente ni précipitation.
                </p>
                <p class="news-text">
                  La prise de rendez-vous sera simple et flexible : vous pourrez réserver votre créneau
                  directement par téléphone ou via notre site internet. Notre système de réservation en
                  ligne vous permettra de choisir facilement le jour et l'heure qui vous conviennent le
                  mieux, ainsi que la prestation souhaitée.
                </p>
                <p class="news-text">
                  Nous vous recommandons de prendre rendez-vous à l'avance pour assurer la disponibilité
                  du créneau de votre choix. Notre équipe reste à votre disposition pour toute question
                  concernant les réservations ou nos différentes prestations.
                </p>
              </div>
            </article>
          </div>
        </div>

        <button class="nav-arrow nav-arrow-right" @click="nextSlide" :disabled="currentSlide === newsArticles.length - 1">
          <ChevronRightIcon class="arrow-icon" />
        </button>
      </div>

      <div class="carousel-dots">
        <span
          v-for="(article, index) in newsArticles"
          :key="index"
          class="dot"
          :class="{ active: currentSlide === index }"
          @click="goToSlide(index)"
        ></span>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import { ChevronLeftIcon, ChevronRightIcon } from '@heroicons/vue/24/outline'

const currentSlide = ref(0)
const windowWidth = ref(window.innerWidth)
const touchStartX = ref(0)
const touchEndX = ref(0)
const isDragging = ref(false)

const newsArticles = ref([
  { id: 1, title: 'Ouverture du salon' },
  { id: 2, title: 'Prise de rendez-vous' }
])

const updateWindowWidth = () => {
  windowWidth.value = window.innerWidth
}

const handleTouchStart = (e) => {
  touchStartX.value = e.touches[0].clientX
  isDragging.value = true
}

const handleTouchMove = (e) => {
  if (!isDragging.value) return
  touchEndX.value = e.touches[0].clientX
}

const handleTouchEnd = () => {
  if (!isDragging.value) return
  isDragging.value = false

  const swipeThreshold = 50
  const diff = touchStartX.value - touchEndX.value

  if (Math.abs(diff) > swipeThreshold) {
    if (diff > 0) {
      nextSlide()
    } else {
      prevSlide()
    }
  }

  touchStartX.value = 0
  touchEndX.value = 0
}

onMounted(() => {
  window.addEventListener('resize', updateWindowWidth)
})

onUnmounted(() => {
  window.removeEventListener('resize', updateWindowWidth)
})

const trackTransform = computed(() => {
  const isMobile = windowWidth.value <= 768
  const isTablet = windowWidth.value <= 1024 && windowWidth.value > 768

  let cardWidth = 49
  let gap = 2.5

  if (isMobile) {
    cardWidth = 94
    gap = 6
  } else if (isTablet) {
    cardWidth = 70
    gap = 2
  }

  return {
    transform: `translateX(calc(-${currentSlide.value * (cardWidth + gap)}vw))`
  }
})

const nextSlide = () => {
  if (currentSlide.value < newsArticles.value.length - 1) {
    currentSlide.value++
  }
}

const prevSlide = () => {
  if (currentSlide.value > 0) {
    currentSlide.value--
  }
}

const goToSlide = (index) => {
  currentSlide.value = index
}
</script>

<style scoped>
.news {
  width: 100%;
  background-color: #212121;
  padding: 80px 40px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.news-container {
  max-width: 1000px;
  width: 90%;
}

.news-title {
  text-align: center;
  color: #FFFFFF;
  font-size: 3rem;
  margin-bottom: 60px;
  font-family: 'Abril Fatface', serif;
  letter-spacing: 2px;
  text-transform: uppercase;
}

.news-carousel-wrapper {
  position: relative;
  display: flex;
  align-items: center;
  gap: 20px;
  margin-bottom: 30px;
}

.news-carousel {
  overflow: hidden;
  flex: 1;
  touch-action: pan-y;
  -webkit-overflow-scrolling: touch;
}

.news-track {
  display: flex;
  transition: transform 0.5s ease-in-out;
  gap: 2.5vw;
}

.nav-arrow {
  background-color: transparent;
  border: 2px solid #d1ae5f;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
  flex-shrink: 0;
}

.nav-arrow:hover:not(:disabled) {
  background-color: #d1ae5f;
  transform: scale(1.1);
}

.nav-arrow:disabled {
  opacity: 0.3;
  cursor: not-allowed;
}

.arrow-icon {
  width: 24px;
  height: 24px;
  color: #d1ae5f;
}

.nav-arrow:hover:not(:disabled) .arrow-icon {
  color: #000000;
}

.news-card {
  width: 49vw;
  min-width: 49vw;
  max-width: 49vw;
  background-color: #1a1a1a;
  border: 2px solid #d1ae5f;
  border-radius: 0;
  overflow: visible;
  margin-top: 5px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  flex-shrink: 0;
}

.news-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(209, 174, 95, 0.3);
}

.news-image {
  width: 100%;
  height: 400px;
  overflow: hidden;
}

.news-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.news-card:hover .news-image img {
  transform: scale(1.05);
}

.news-content {
  padding: 40px;
}

.news-card-title {
  color: #FFFFFF;
  font-size: 2rem;
  font-family: 'Abril Fatface', serif;
  margin-bottom: 25px;
  letter-spacing: 1px;
}

.news-text {
  color: #c0c0c0;
  font-size: 1.1rem;
  line-height: 1.8;
  margin-bottom: 20px;
}

.news-text:last-child {
  margin-bottom: 0;
}

.carousel-dots {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-top: 20px;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background-color: #4a4a4a;
  cursor: pointer;
  transition: all 0.3s ease;
}

.dot.active {
  background-color: #d1ae5f;
  transform: scale(1.2);
}

.dot:hover {
  background-color: #d1ae5f;
}

@media (max-width: 1024px) {
  .news-card {
    width: 70vw;
    min-width: 70vw;
    max-width: 70vw;
  }

  .news-track {
    gap: 2vw;
  }
}

@media (max-width: 768px) {
  .news {
    padding: 60px 0;
  }

  .news-container {
    max-width: 100%;
    width: 100%;
  }

  .news-title {
    font-size: 2rem;
    margin-bottom: 40px;
    padding: 0 20px;
  }

  .news-carousel-wrapper {
    gap: 0;
  }

  .news-carousel {
    cursor: grab;
  }

  .news-carousel:active {
    cursor: grabbing;
  }

  .news-card {
    width: 94vw;
    min-width: 94vw;
    max-width: 94vw;
    margin: 5px 3vw 0;
    border-radius: 0;
  }

  .news-track {
    gap: 0;
  }

  .nav-arrow {
    display: none;
  }

  .news-image {
    height: 250px;
  }

  .news-content {
    padding: 30px 20px;
  }

  .news-card-title {
    font-size: 1.5rem;
  }

  .news-text {
    font-size: 1rem;
  }

  .carousel-dots {
    padding: 0 20px;
  }
}
</style>
