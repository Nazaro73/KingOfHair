<template>
  <section class="pricing">
    <div class="pricing-container">
      <h2 class="pricing-title">Nos Services & Tarifs</h2>
      <div class="pricing-grid">
        <div class="pricing-item">
          <div class="pricing-header">
            <h3 class="pricing-name">Coupe</h3>
            <span class="pricing-price">15 €</span>
          </div>
          <div class="pricing-separator"></div>
          <p class="pricing-description">Coupe aux ciseaux et au rasoir pour un résultat net, précis et parfaitement adapté à votre style.</p>
        </div>

        <div class="pricing-item">
          <div class="pricing-header">
            <h3 class="pricing-name">Coupe + Barbe + Shampoing</h3>
            <span class="pricing-price">20 €</span>
          </div>
          <div class="pricing-separator"></div>
          <p class="pricing-description">Profitez d'un service complet : une coupe soignée, une taille de barbe sur mesure et un shampoing rafraîchissant pour une finition impeccable.</p>
        </div>

        <div class="pricing-item">
          <div class="pricing-header">
            <h3 class="pricing-name">Soin du visage + Coupe</h3>
            <span class="pricing-price">20 €</span>
          </div>
          <div class="pricing-separator"></div>
          <p class="pricing-description">Offrez-vous un moment de détente avec un soin du visage revitalisant suivi d'une coupe élégante pour un look frais et soigné.</p>
        </div>

        <div class="pricing-item">
          <div class="pricing-header">
            <h3 class="pricing-name">Formule Complète</h3>
            <span class="pricing-price">25 €</span>
          </div>
          <div class="pricing-separator"></div>
          <p class="pricing-description">Le service premium tout compris : coupe, barbe, shampoing et soin du visage pour une expérience complète et relaxante.</p>
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
