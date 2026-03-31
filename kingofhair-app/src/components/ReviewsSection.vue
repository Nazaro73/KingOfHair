<template>
  <section id="avis" class="reviews">
    <div class="reviews-container">
      <p class="reviews-subtitle">Ce que nos clients pensent de nous</p>
      <h2 class="reviews-title">Avis Clients<br><span class="reviews-title-sub">KING of Hair – Coiffeur Chambéry</span></h2>

      <div class="reviews-rating">
        <div class="stars">
          <span class="star">★</span>
          <span class="star">★</span>
          <span class="star">★</span>
          <span class="star">★</span>
          <span class="star">★</span>
        </div>
        <p class="rating-text">5.0 sur Google · 125 avis</p>
      </div>

      <div class="reviews-carousel">
        <div class="reviews-track" :style="{ transform: `translateX(calc(-${currentSlide * 100}% - ${currentSlide * 20}px))` }">
          <div v-for="(review, index) in reviews" :key="index" class="review-card">
            <div class="review-header">
              <div class="review-author">
                <p class="author-name">{{ review.name }}</p>
                <p class="review-date">{{ review.date }}</p>
              </div>
              <div class="review-stars">
                <span class="star">★</span>
                <span class="star">★</span>
                <span class="star">★</span>
                <span class="star">★</span>
                <span class="star">★</span>
              </div>
            </div>
            <p class="review-text">{{ review.text }}</p>
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
    name: "Jonathan M.",
    date: "Il y a 2 mois",
    text: "Excellent salon à Chambéry ! Le coiffeur est très professionnel, à l'écoute et prend vraiment le temps de comprendre ce qu'on veut. La coupe est toujours impeccable et l'accueil super sympa. Je recommande à 100% !"
  },
  {
    name: "Ridouan JEBARI",
    date: "Il y a 2 mois",
    text: "Je suis allé dans ce salon récemment. L'équipe est très sympathique et accueillante. Le coiffeur est à l'écoute et prend le temps de bien comprendre ce que l'on souhaite. Le résultat est au-delà de mes attentes, une coupe parfaite ! Je recommande vivement ce salon pour son professionnalisme."
  },
  {
    name: "Marwan Mato",
    date: "Il y a 2 mois",
    text: "Très professionnel, le coiffeur est superbe aimable et très sympa. Je suis très satisfait de ma coupe et de ma barbe. Je recommande à 100% !"
  },
  {
    name: "Bastien L",
    date: "Il y a 2 mois",
    text: "Toujours un plaisir de venir dans ce salon ! Le coiffeur est très professionnel et à l'écoute. Le résultat est parfait, je recommande à tout le monde !"
  },
  {
    name: "Yasmin",
    date: "Il y a 2 mois",
    text: "Super salon ! Le coiffeur est super. Mon fils est ressorti content de sa coupe 👍 Du coup monsieur s'est aussi fait coiffer. Et il est ressorti super content de sa coupe aussi. Il a pris le temps de leur faire des coupes au top. Je recommande !!"
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
  line-height: 1.3;
}

.reviews-title-sub {
  display: block;
  font-size: 1.8rem;
  color: #d1ae5f;
  letter-spacing: 3px;
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

.review-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  padding-bottom: 15px;
  border-bottom: 1px solid #d1ae5f;
}

.review-stars {
  flex-shrink: 0;
  display: flex;
  align-items: center;
}

.review-stars .star {
  color: #d1ae5f;
  font-size: 1.2rem;
  margin-right: 3px;
  line-height: 1;
}

.review-author {
  display: flex;
  flex-direction: column;
  gap: 3px;
}

.review-text {
  color: #333333;
  font-size: 1.1rem;
  line-height: 1.8;
  font-style: italic;
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
