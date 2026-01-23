<template>
  <section id="accueil" class="hero">
    <video autoplay loop muted playsinline class="hero-video">
      <source src="@/assets/1029.mp4" type="video/mp4">
    </video>
    <div class="hero-overlay"></div>
    <div class="hero-content">
      <h1 class="hero-title">
        <span class="sr-only">King of Hair - Coiffeur Barbier à Chambéry, salon de coiffure pour hommes en Savoie</span>
        <img src="@/assets/logo-kingofhair.png" alt="King of Hair - Votre coiffeur barbier à Chambéry, salon de coiffure pour hommes en Savoie" class="hero-logo">
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

.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

@media (max-width: 768px) {
  .hero-logo {
    max-height: 40vh;
  }
}
</style>
