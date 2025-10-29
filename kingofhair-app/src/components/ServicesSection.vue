<template>
  <section id="services" class="services">
    <div class="services-container">
      <h2 class="services-title">Nos Prestations</h2>
      <div class="services-grid">
        <div class="service-card">
          <div class="service-icon">
            <img src="@/assets/icon/icon scissors.svg" alt="Scissors" class="icon" />
          </div>
          <h3 class="service-name">Coupe de cheveux & Taille de barbe</h3>
          <p class="service-description">Offrez-vous une coupe élégante et une barbe parfaitement taillée. Un soin complet pour un look soigné et moderne.</p>
        </div>

        <div class="service-card">
          <div class="service-icon">
            <img src="@/assets/icon/icon razor.svg" alt="Razor" class="icon" />
          </div>
          <h3 class="service-name">Soin de la barbe</h3>
          <p class="service-description">Entretenez votre barbe avec des soins professionnels : nettoyage, hydratation, taille et mise en forme pour une barbe saine et élégante.</p>
        </div>

        <div class="service-card">
          <div class="service-icon">
            <img src="@/assets/icon/icon beard.svg" alt="Beard" class="icon" />
          </div>
          <h3 class="service-name">Rasage traditionnel</h3>
          <p class="service-description">Découvrez l'art du rasage traditionnel à la lame pour une peau parfaitement lisse et un moment de détente absolue.</p>
        </div>

        <div class="service-card">
          <div class="service-icon">
            <img src="@/assets/icon/icon facial.svg" alt="Facial" class="icon" />
          </div>
          <h3 class="service-name">Soin du visage</h3>
          <p class="service-description">Nettoyez, hydratez et revitalisez votre peau grâce à un soin facial complet et apaisant.</p>
        </div>

        <div class="service-card">
          <div class="service-icon">
            <img src="@/assets/icon/icon_ ustache.svg" alt="Mustache" class="icon" />
          </div>
          <h3 class="service-name">Taille de moustache</h3>
          <p class="service-description">Une mise en forme précise de votre moustache pour un style net et parfaitement équilibré.</p>
        </div>

        <div class="service-card">
          <div class="service-icon">
            <img src="@/assets/icon/icon hair.svg" alt="Hair" class="icon" />
          </div>
          <h3 class="service-name">Coiffure & Styling</h3>
          <p class="service-description">Donnez forme à vos cheveux avec un coiffage professionnel adapté à votre style et à votre personnalité.</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
.services {
  width: 100%;
  background-color: #000000;
  padding: 80px 20px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.services-container {
  max-width: 1200px;
  width: 100%;
}

.services-title {
  text-align: center;
  color: #FFFFFF;
  font-size: 3rem;
  margin-bottom: 60px;
  font-family: 'Abril Fatface', serif;
  text-transform: uppercase;
  letter-spacing: 2px;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 40px;
  padding: 0 20px;
}

.service-card {
  background-color: #1a1a1a;
  border: 2px solid #d1ae5f;
  border-radius: 20px;
  padding: 50px 40px;
  text-align: center;
  transition: all 0.4s ease;
  cursor: pointer;
  position: relative;
  overflow: hidden;
}

.service-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 3px;
  background: linear-gradient(90deg, transparent, #d1ae5f, transparent);
  transition: left 0.6s ease;
}

.service-card:hover::before {
  left: 100%;
}

.service-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 50px rgba(209, 174, 95, 0.2);
  border-color: #d1ae5f;
  background-color: #0d0d0d;
}

.service-icon {
  margin-bottom: 25px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.icon {
  width: 80px;
  height: 80px;
  object-fit: contain;
  transition: all 0.3s ease;
}

.service-card:hover .icon {
  transform: scale(1.15);
  filter: drop-shadow(0 0 12px rgba(209, 174, 95, 0.6));
}

.service-name {
  color: #FFFFFF;
  font-size: 1.5rem;
  font-family: 'Abril Fatface', serif;
  margin-bottom: 20px;
  text-align: center;
  letter-spacing: 0.5px;
  line-height: 1.4;
}

.service-description {
  color: #c0c0c0;
  font-size: 1rem;
  line-height: 1.7;
  text-align: center;
  margin-top: 15px;
  font-weight: 300;
}

@media (max-width: 768px) {
  .services {
    padding: 60px 15px;
  }

  .services-title {
    font-size: 2rem;
    margin-bottom: 40px;
  }

  .services-grid {
    grid-template-columns: 1fr;
    gap: 30px;
    padding: 0;
  }

  .service-card {
    padding: 30px 20px;
  }

  .service-name {
    font-size: 1.2rem;
  }

  .service-description {
    font-size: 0.9rem;
  }

  .icon {
    width: 60px;
    height: 60px;
  }
}
</style>
