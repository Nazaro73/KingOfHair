<template>
  <section id="accueil" class="hero">
    <video autoplay loop muted playsinline class="hero-video">
      <source src="@/assets/1029.mp4" type="video/mp4">
    </video>
    <div class="hero-overlay"></div>
    <div class="hero-content">
      <h1 class="hero-title">
        <img src="@/assets/logo-kingofhair.png" alt="King of Hair - Votre coiffeur barbier à Chambéry, salon de coiffure pour hommes en Savoie" class="hero-logo">
        <span class="hero-subtitle">Coiffeur Barbier à Chambéry</span>
      </h1>
    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
.hero {
  position: relative;
  width: 100%;
  height: 100vh;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
}

.hero-video {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100%;
  height: 100%;
  transform: translate(-50%, -50%);
  z-index: 1;
  object-fit: cover;
}

.hero-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.3);
  z-index: 2;
}

.hero-content {
  position: relative;
  z-index: 3;
  display: flex;
  align-items: center;
  justify-content: center;
}

.hero-logo {
  max-height: 50vh;
  width: auto;
  height: auto;
  animation: fadeIn 1.5s ease-in-out;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: scale(0.9);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

.hero-title {
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.hero-subtitle {
  color: #d1ae5f;
  font-family: 'Abril Fatface', serif;
  font-size: 1.8rem;
  letter-spacing: 4px;
  text-transform: uppercase;
  margin-top: 20px;
  animation: fadeIn 2s ease-in-out;
}

@media (max-width: 768px) {
  .hero-logo {
    max-height: 40vh;
  }

  .hero-subtitle {
    font-size: 1.2rem;
    letter-spacing: 2px;
  }
}
</style>
