<template>
  <section id="avis" class="reviews">
    <div class="reviews-container">
      <p class="reviews-subtitle">Ce que nos clients pensent de nous</p>
      <h2 class="reviews-title">Avis de nos clients</h2>

      <div class="reviews-rating">
        <div class="stars">
          <span class="star">★</span>
          <span class="star">★</span>
          <span class="star">★</span>
          <span class="star">★</span>
          <span class="star">★</span>
        </div>
        <p class="rating-text">5.0 sur Google · 70 avis</p>
      </div>

      <div class="reviews-carousel">
        <div class="reviews-track" :style="{ transform: `translateX(calc(-${currentSlide * 100}% - ${currentSlide * 20}px))` }">
          <div v-for="(review, index) in reviews" :key="index" class="review-card">
            <div class="review-stars">
              <span class="star">★</span>
              <span class="star">★</span>
              <span class="star">★</span>
              <span class="star">★</span>
              <span class="star">★</span>
            </div>
            <p class="review-text">{{ review.text }}</p>
            <div class="review-author">
              <p class="author-name">{{ review.name }}</p>
              <p class="review-date">{{ review.date }}</p>
            </div>
          </div>
        </div>
      </div>

      <div class="carousel-dots">
        <span
          v-for="(review, index) in reviews"
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
import { ref, onMounted, onUnmounted } from 'vue'

const currentSlide = ref(0)
let interval = null

const reviews = [
  {
    name: "Thomas Martin",
    date: "Il y a 2 semaines",
    text: "Excellente expérience ! La coupe est impeccable et l'accueil très chaleureux. Je recommande vivement ce salon de coiffure. Un vrai professionnel qui prend le temps de bien faire les choses."
  },
  {
    name: "Lucas Dubois",
    date: "Il y a 1 mois",
    text: "Meilleur barbier de la région ! Toujours un travail soigné et une ambiance conviviale. La taille de barbe est parfaite à chaque fois. Je ne vais plus ailleurs depuis 2 ans."
  },
  {
    name: "Antoine Bernard",
    date: "Il y a 3 semaines",
    text: "Service au top, très professionnel et à l'écoute. Le rasage traditionnel est exceptionnel, une vraie expérience de détente. Le rapport qualité-prix est imbattable."
  },
  {
    name: "Maxime Rousseau",
    date: "Il y a 1 semaine",
    text: "Super accueil et travail impeccable ! J'ai essayé le soin du visage avec la coupe, c'était parfait. L'attention aux détails fait toute la différence. Je reviens sans hésiter."
  },
  {
    name: "Pierre Lefebvre",
    date: "Il y a 2 mois",
    text: "Je viens régulièrement et je ne suis jamais déçu. La qualité du service est constante et les conseils sont toujours pertinents. Ambiance détendue et professionnelle à la fois."
  },
  {
    name: "Alexandre Moreau",
    date: "Il y a 3 jours",
    text: "Coupe moderne et soignée, exactement ce que je voulais ! Le coiffeur a su comprendre mes attentes et les dépasser. Un grand professionnalisme et une vraie passion du métier."
  }
]

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % reviews.length
}

const goToSlide = (index) => {
  currentSlide.value = index
  resetInterval()
}

const resetInterval = () => {
  if (interval) {
    clearInterval(interval)
  }
  interval = setInterval(nextSlide, 5000)
}

onMounted(() => {
  interval = setInterval(nextSlide, 5000)
})

onUnmounted(() => {
  if (interval) {
    clearInterval(interval)
  }
})
</script>

<style scoped>
.reviews {
  width: 100%;
  background-color: #FFFFFF;
  padding: 80px 40px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.reviews-container {
  max-width: 800px;
  width: 100%;
}

.reviews-subtitle {
  text-align: center;
  color: #d1ae5f;
  font-size: 1.1rem;
  margin-bottom: 15px;
  letter-spacing: 1px;
  text-transform: uppercase;
  font-weight: 500;
}

.reviews-title {
  text-align: center;
  color: #000000;
  font-size: 3rem;
  margin-bottom: 30px;
  font-family: 'Abril Fatface', serif;
  letter-spacing: 2px;
  text-transform: uppercase;
}

.reviews-rating {
  text-align: center;
  margin-bottom: 60px;
}

.stars {
  font-size: 2rem;
  margin-bottom: 10px;
}

.star {
  color: #d1ae5f;
  margin: 0 2px;
}

.rating-text {
  color: #666666;
  font-size: 1.1rem;
  font-weight: 500;
}

.reviews-carousel {
  overflow: hidden;
  width: 100%;
  margin-bottom: 30px;
  padding: 0 10px;
}

.reviews-track {
  display: flex;
  transition: transform 0.5s ease-in-out;
  gap: 20px;
}

.review-card {
  width: 100%;
  min-height: 350px;
  padding: 50px 40px;
  background-color: #f8f8f8;
  border-radius: 15px;
  border-left: 4px solid #d1ae5f;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  flex-shrink: 0;
}

.review-stars {
  margin-bottom: 20px;
}

.review-stars .star {
  color: #d1ae5f;
  font-size: 1.2rem;
  margin-right: 3px;
}

.review-text {
  color: #333333;
  font-size: 1.1rem;
  line-height: 1.8;
  margin-bottom: 25px;
  font-style: italic;
}

.review-author {
  border-top: 1px solid #d1ae5f;
  padding-top: 20px;
}

.author-name {
  color: #000000;
  font-size: 1.1rem;
  font-weight: 600;
  margin-bottom: 5px;
}

.review-date {
  color: #999999;
  font-size: 0.9rem;
}

.carousel-dots {
  display: flex;
  justify-content: center;
  gap: 10px;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background-color: #d0d0d0;
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

@media (max-width: 768px) {
  .reviews {
    padding: 60px 20px;
  }

  .reviews-title {
    font-size: 2rem;
  }

  .reviews-subtitle {
    font-size: 1rem;
  }

  .review-card {
    width: 100%;
    padding: 30px 20px;
  }

  .review-text {
    font-size: 1rem;
  }

  .stars {
    font-size: 1.5rem;
  }
}
</style>
