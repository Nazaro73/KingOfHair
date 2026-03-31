<template>
  <section id="reservation" class="booking-section">
    <div class="booking-container">
      <h2 class="booking-title">Réservez chez votre Coiffeur à Chambéry</h2>
      <p class="booking-subtitle">Prenez rendez-vous en ligne en quelques clics chez King of Hair</p>

      <div class="booking-content">
        <div class="booking-info">
          <div class="info-item">
            <div class="info-icon">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v6h4.5m4.5 0a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
              </svg>
            </div>
            <div class="info-text">
              <h4>Rapide & Simple</h4>
              <p>Réservez en moins de 2 minutes</p>
            </div>
          </div>

          <div class="info-item">
            <div class="info-icon">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" d="M6.75 3v2.25M17.25 3v2.25M3 18.75V7.5a2.25 2.25 0 0 1 2.25-2.25h13.5A2.25 2.25 0 0 1 21 7.5v11.25m-18 0A2.25 2.25 0 0 0 5.25 21h13.5A2.25 2.25 0 0 0 21 18.75m-18 0v-7.5A2.25 2.25 0 0 1 5.25 9h13.5A2.25 2.25 0 0 1 21 11.25v7.5" />
              </svg>
            </div>
            <div class="info-text">
              <h4>Disponibilités en temps réel</h4>
              <p>Choisissez le créneau qui vous convient</p>
            </div>
          </div>

          <div class="info-item">
            <div class="info-icon">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" d="M14.857 17.082a23.848 23.848 0 0 0 5.454-1.31A8.967 8.967 0 0 1 18 9.75V9A6 6 0 0 0 6 9v.75a8.967 8.967 0 0 1-2.312 6.022c1.733.64 3.56 1.085 5.455 1.31m5.714 0a24.255 24.255 0 0 1-5.714 0m5.714 0a3 3 0 1 1-5.714 0" />
              </svg>
            </div>
            <div class="info-text">
              <h4>Rappel automatique</h4>
              <p>Recevez un SMS de confirmation</p>
            </div>
          </div>
        </div>

        <div class="booking-widget">
          <img src="@/assets/planitylogo.png" alt="Planity" class="planity-logo" />
          <a
            href="https://www.planity.com/king-of-hair-73000-chambery"
            target="_blank"
            rel="noopener noreferrer"
            class="booking-button"
          >
            <span class="button-text">Prendre rendez-vous</span>
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="button-icon">
              <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5 21 12m0 0-7.5 7.5M21 12H3" />
            </svg>
          </a>
          <p class="booking-note">Réservation sécurisée via Planity</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
.booking-section {
  background-color: #000000;
  padding: 100px 40px;
  position: relative;
  overflow: hidden;
}

.booking-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, #d1ae5f, transparent);
}

.booking-container {
  max-width: 1200px;
  margin: 0 auto;
  text-align: center;
}

.booking-title {
  font-family: 'Abril Fatface', serif;
  font-size: 3rem;
  color: #ffffff;
  margin-bottom: 15px;
  letter-spacing: 2px;
}

.booking-subtitle {
  font-family: 'Inter', sans-serif;
  font-size: 1.2rem;
  color: #999;
  margin-bottom: 60px;
}

.booking-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 60px;
}

.booking-info {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.info-item {
  display: flex;
  align-items: center;
  gap: 20px;
  text-align: left;
  padding: 15px 0;
  transition: all 0.3s ease;
}

.info-item:hover {
  transform: translateX(10px);
}

.info-icon {
  width: 50px;
  height: 50px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #ffffff;
  border-radius: 50%;
  color: #000;
}

.info-icon svg {
  width: 24px;
  height: 24px;
}

.info-text h4 {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  font-weight: 600;
  color: #fff;
  margin: 0 0 5px 0;
}

.info-text p {
  font-family: 'Inter', sans-serif;
  font-size: 0.95rem;
  color: #888;
  margin: 0;
}

.booking-widget {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 60px;
  background: rgba(0, 0, 0, 0.5);
  border-radius: 20px;
  border: 2px solid rgba(255, 255, 255, 0.3);
}

.planity-logo {
  width: 180px;
  height: auto;
  margin-bottom: 30px;
}

.booking-button {
  display: inline-flex;
  align-items: center;
  gap: 15px;
  padding: 20px 50px;
  background: #ffffff;
  color: #000;
  text-decoration: none;
  font-family: 'Inter', sans-serif;
  font-size: 1.3rem;
  font-weight: 700;
  border-radius: 50px;
  transition: all 0.3s ease;
  box-shadow: 0 10px 30px rgba(255, 255, 255, 0.2);
}

.booking-button:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 40px rgba(255, 255, 255, 0.3);
}

.button-icon {
  width: 24px;
  height: 24px;
  transition: transform 0.3s ease;
}

.booking-button:hover .button-icon {
  transform: translateX(5px);
}

.booking-note {
  font-family: 'Inter', sans-serif;
  font-size: 0.85rem;
  color: #666;
  margin-top: 20px;
}

@media (max-width: 1024px) {
  .booking-content {
    flex-direction: column;
    gap: 40px;
  }

  .booking-info {
    width: 100%;
  }

  .booking-widget {
    width: 100%;
    padding: 40px;
  }
}

@media (max-width: 768px) {
  .booking-section {
    padding: 60px 20px;
  }

  .booking-title {
    font-size: 2rem;
  }

  .booking-subtitle {
    font-size: 1rem;
    margin-bottom: 40px;
  }

  .info-item {
    padding: 20px;
  }

  .info-item:hover {
    transform: none;
  }

  .booking-button {
    padding: 18px 35px;
    font-size: 1.1rem;
  }
}
</style>
