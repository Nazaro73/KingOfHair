<template>
  <section id="tarifs" class="pricing">
    <div class="pricing-container">
      <h2 class="pricing-title">Tarifs Coiffure & Barbe</h2>
      <div class="pricing-grid">
        <div class="pricing-item">
          <div class="pricing-header">
            <h3 class="pricing-name">Coupe de cheveux <span class="pricing-duration">30min</span></h3>
            <span class="pricing-price">18 €</span>
          </div>
          <div class="pricing-separator"></div>
          <p class="pricing-description">Une coupe soignée et précise, adaptée à votre style et à la forme de votre visage.</p>
        </div>

        <div class="pricing-item">
          <div class="pricing-header">
            <h3 class="pricing-name">Barbe <span class="pricing-duration">20min</span></h3>
            <span class="pricing-price">10 €</span>
          </div>
          <div class="pricing-separator"></div>
          <p class="pricing-description">Taille et entretien de votre barbe pour un look impeccable et bien défini.</p>
        </div>

        <div class="pricing-item">
          <div class="pricing-header">
            <h3 class="pricing-name">Coupe enfant <span class="pricing-duration">30min</span></h3>
            <span class="pricing-price">15 €</span>
          </div>
          <div class="pricing-separator"></div>
          <p class="pricing-description">Une coupe adaptée aux plus jeunes, réalisée avec patience et attention.</p>
        </div>

        <div class="pricing-item">
          <div class="pricing-header">
            <h3 class="pricing-name">Cheveux et barbe <span class="pricing-duration">45min</span></h3>
            <span class="pricing-price">25 €</span>
          </div>
          <div class="pricing-separator"></div>
          <p class="pricing-description">La formule complète : coupe de cheveux et taille de barbe pour un look parfait.</p>
        </div>

        <div class="pricing-item">
          <div class="pricing-header">
            <h3 class="pricing-name">Soin de visage <span class="pricing-duration">15min</span></h3>
            <span class="pricing-price">10 €</span>
          </div>
          <div class="pricing-separator"></div>
          <p class="pricing-description">Nettoyez et revitalisez votre peau grâce à un soin facial apaisant.</p>
        </div>

        <div class="pricing-item">
          <div class="pricing-header">
            <h3 class="pricing-name">Défrisage <span class="pricing-duration">30min</span></h3>
            <span class="pricing-price">10 €</span>
          </div>
          <div class="pricing-separator"></div>
          <p class="pricing-description">Lissez vos cheveux pour un résultat naturel et durable.</p>
        </div>

        <div class="pricing-item">
          <div class="pricing-header">
            <h3 class="pricing-name">Kératine ou protéine <span class="pricing-duration">1h 30min</span></h3>
            <span class="pricing-price">Sur devis</span>
          </div>
          <div class="pricing-separator"></div>
          <p class="pricing-description">Traitement professionnel pour des cheveux lisses, brillants et en pleine santé.</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
.pricing {
  width: 100%;
  background-color: #212121;
  padding: 80px 40px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.pricing-container {
  max-width: 1400px;
  width: 100%;
}

.pricing-title {
  text-align: center;
  color: #FFFFFF;
  font-size: 3rem;
  margin-bottom: 60px;
  font-family: 'Abril Fatface', serif;
  letter-spacing: 1px;
}

.pricing-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 50px 60px;
  padding: 0;
}

.pricing-item {
  background-color: transparent;
  padding: 0;
}

.pricing-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 15px;
}

.pricing-name {
  color: #FFFFFF;
  font-size: 1.3rem;
  font-family: 'Abril Fatface', serif;
  margin: 0;
  letter-spacing: 0.5px;
}

.pricing-price {
  color: #FFFFFF;
  font-size: 1.3rem;
  font-weight: 600;
  white-space: nowrap;
}

.pricing-separator {
  width: 100%;
  height: 1px;
  background: linear-gradient(90deg, #d1ae5f 0%, #d1ae5f 100%);
  margin-bottom: 15px;
}

.pricing-description {
  color: #FFFFFF;
  font-size: 1rem;
  line-height: 1.8;
  text-align: left;
  margin: 0;
  font-weight: 300;
}

.pricing-duration {
  color: #888;
  font-weight: 400;
  font-size: 0.85rem;
  font-family: 'Inter', sans-serif;
  margin-left: 8px;
}

@media (max-width: 1024px) {
  .pricing-grid {
    grid-template-columns: 1fr;
    gap: 40px;
  }
}

@media (max-width: 768px) {
  .pricing {
    padding: 60px 20px;
  }

  .pricing-title {
    font-size: 2rem;
    margin-bottom: 40px;
  }

  .pricing-name {
    font-size: 1.1rem;
  }

  .pricing-price {
    font-size: 1.1rem;
  }

  .pricing-description {
    font-size: 0.95rem;
  }
}
</style>
