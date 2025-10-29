<template>
  <footer class="footer">
    <div class="footer-container">
      <h2 class="footer-title">CONTACTEZ NOUS</h2>

      <div class="footer-content">
        <div class="contact-item">
          <MapPinIcon class="contact-icon" />
          <div class="contact-info">
            <h3 class="contact-label">Adresse</h3>
            <p class="contact-text">123 Rue de Chambéry</p>
            <p class="contact-text">73000 Chambéry, France</p>
          </div>
        </div>

        <div class="contact-item">
          <PhoneIcon class="contact-icon" />
          <div class="contact-info">
            <h3 class="contact-label">Téléphone</h3>
            <a href="tel:+33123456789" class="contact-link">+33 1 23 45 67 89</a>
          </div>
        </div>

        <div class="contact-item">
          <EnvelopeIcon class="contact-icon" />
          <div class="contact-info">
            <h3 class="contact-label">Email</h3>
            <a href="mailto:contact@kingofhair.fr" class="contact-link">contact@kingofhair.fr</a>
          </div>
        </div>

        <div class="contact-item">
          <ClockIcon class="contact-icon" />
          <div class="contact-info">
            <h3 class="contact-label">Horaires</h3>
            <p class="contact-text">Lundi - Vendredi : 9h - 19h</p>
            <p class="contact-text">Samedi : 9h - 18h</p>
            <p class="contact-text">Dimanche : Fermé</p>
          </div>
        </div>
      </div>

      <div class="footer-bottom">
        <p class="copyright">&copy; 2024 King of Hair. Tous droits réservés.</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { MapPinIcon, PhoneIcon, EnvelopeIcon, ClockIcon } from '@heroicons/vue/24/outline'
</script>

<style scoped>
.footer {
  width: 100%;
  background-color: #FFFFFF;
  padding: 80px 40px 40px;
}

.footer-container {
  max-width: 1200px;
  margin: 0 auto;
}

.footer-title {
  text-align: center;
  color: #212121;
  font-size: 3rem;
  margin-bottom: 60px;
  font-family: 'Abril Fatface', serif;
  letter-spacing: 2px;
}

.footer-content {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 30px;
  margin-bottom: 60px;
}

.contact-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 15px;
  padding: 30px 20px;
  background-color: #fafafa;
  border-radius: 15px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.contact-item:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(209, 174, 95, 0.2);
}

.contact-icon {
  width: 40px;
  height: 40px;
  color: #d1ae5f;
  flex-shrink: 0;
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 100%;
}

.contact-label {
  color: #212121;
  font-size: 1.4rem;
  font-family: 'Abril Fatface', serif;
  letter-spacing: 1px;
  margin: 0;
}

.contact-text {
  color: #666666;
  font-size: 1rem;
  line-height: 1.6;
  margin: 0;
}

.contact-link {
  color: #666666;
  font-size: 1rem;
  text-decoration: none;
  transition: color 0.3s ease;
}

.contact-link:hover {
  color: #d1ae5f;
}

.footer-bottom {
  border-top: 2px solid #e0e0e0;
  padding-top: 30px;
  text-align: center;
}

.copyright {
  color: #666666;
  font-size: 0.95rem;
  margin: 0;
}

@media (max-width: 1024px) {
  .footer-content {
    grid-template-columns: repeat(2, 1fr);
    gap: 25px;
  }
}

@media (max-width: 768px) {
  .footer {
    padding: 60px 20px 30px;
  }

  .footer-title {
    font-size: 2rem;
    margin-bottom: 40px;
  }

  .footer-content {
    grid-template-columns: 1fr;
    gap: 20px;
    margin-bottom: 40px;
  }

  .contact-item {
    padding: 15px;
  }

  .contact-icon {
    width: 36px;
    height: 36px;
  }

  .contact-label {
    font-size: 1.2rem;
  }

  .contact-text,
  .contact-link {
    font-size: 0.95rem;
  }
}
</style>
