<template>
  <section class="stats" ref="statsSection">
    <div class="stats-container">
      <div class="stat-item">
        <img src="@/assets/icon/icon-scissors-black.svg" alt="Scissors" class="stat-icon" />
        <h3 class="stat-number">{{ animatedCuts }}+</h3>
        <p class="stat-label">Coupes</p>
      </div>

      <div class="stat-item">
        <img src="@/assets/icon/icon-barbershop-black.svg" alt="Barbershop" class="stat-icon" />
        <h3 class="stat-number">{{ animatedClients }}+</h3>
        <p class="stat-label">Clients</p>
      </div>

      <div class="stat-item">
        <StarIcon class="stat-icon star-icon" />
        <h3 class="stat-number">{{ animatedReviews }}+</h3>
        <p class="stat-label">Avis</p>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { StarIcon } from '@heroicons/vue/24/outline'

const statsSection = ref(null)
const animatedCuts = ref(0)
const animatedClients = ref(0)
const animatedReviews = ref(0)
const hasAnimated = ref(false)

const targetCuts = 3000
const targetClients = 200
const targetReviews = 70

const animateValue = (start, end, duration, callback) => {
  const startTime = performance.now()
  const range = end - start

  const step = (currentTime) => {
    const elapsed = currentTime - startTime
    const progress = Math.min(elapsed / duration, 1)

    // Easing function pour un effet plus naturel
    const easeOutQuad = progress * (2 - progress)
    const currentValue = Math.floor(start + range * easeOutQuad)

    callback(currentValue)

    if (progress < 1) {
      requestAnimationFrame(step)
    }
  }

  requestAnimationFrame(step)
}

const handleIntersection = (entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting && !hasAnimated.value) {
      hasAnimated.value = true

      // Animer les compteurs avec des durées différentes
      animateValue(0, targetCuts, 2000, (val) => {
        animatedCuts.value = val
      })

      animateValue(0, targetClients, 2000, (val) => {
        animatedClients.value = val
      })

      animateValue(0, targetReviews, 2000, (val) => {
        animatedReviews.value = val
      })
    }
  })
}

let observer = null

onMounted(() => {
  observer = new IntersectionObserver(handleIntersection, {
    threshold: 0.3
  })

  if (statsSection.value) {
    observer.observe(statsSection.value)
  }
})

onUnmounted(() => {
  if (observer && statsSection.value) {
    observer.unobserve(statsSection.value)
  }
})
</script>

<style scoped>
.stats {
  width: 100%;
  background-color: #d1ae5f;
  padding: 80px 40px;
}

.stats-container {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 60px;
}

.stat-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 20px;
}

.stat-icon {
  width: 80px;
  height: 80px;
  color: #000000;
  transition: transform 0.3s ease;
}

.star-icon {
  color: #000000;
  filter: none;
  stroke-width: 1.5;
}

.stat-item:hover .stat-icon {
  transform: scale(1.1);
}

.stat-number {
  color: #000000;
  font-size: 3.5rem;
  font-family: 'Abril Fatface', serif;
  margin: 0;
  letter-spacing: 2px;
}

.stat-label {
  color: #000000;
  font-size: 1.5rem;
  font-family: 'Abril Fatface', serif;
  text-transform: uppercase;
  letter-spacing: 2px;
  margin: 0;
}

@media (max-width: 1024px) {
  .stats-container {
    gap: 40px;
  }

  .stat-icon {
    width: 70px;
    height: 70px;
  }

  .stat-number {
    font-size: 3rem;
  }

  .stat-label {
    font-size: 1.3rem;
  }
}

@media (max-width: 768px) {
  .stats {
    padding: 60px 20px;
  }

  .stats-container {
    grid-template-columns: 1fr;
    gap: 50px;
  }

  .stat-icon {
    width: 60px;
    height: 60px;
  }

  .stat-number {
    font-size: 2.5rem;
  }

  .stat-label {
    font-size: 1.2rem;
  }
}
</style>
