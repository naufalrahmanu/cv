<template>
  <section id="about" class="section about">
    <div class="container">
      <h2 class="section-title">Tentang Saya</h2>
      <div class="about-content">
        <div class="about-text">
          <p>
            Saya adalah seorang Web Developer dengan pengalaman 2+ tahun dalam mengembangkan 
            website dan aplikasi web menggunakan teknologi modern seperti Vue.js, React, dan Node.js.
          </p>
          <p>
            Saya memiliki passion dalam menciptakan solusi digital yang tidak hanya menarik secara visual 
            tetapi juga memberikan pengalaman pengguna yang optimal.
          </p>
          <div class="about-info">
            <div class="info-item">
              <strong>Email:</strong>
              <span>email@example.com</span>
            </div>
            <div class="info-item">
              <strong>Lokasi:</strong>
              <span>Kota, Negara</span>
            </div>
            <div class="info-item">
              <strong>Pendidikan:</strong>
              <span>S1 Teknik Informatika</span>
            </div>
            <div class="info-item">
              <strong>Freelance:</strong>
              <span>Available</span>
            </div>
          </div>
          <a href="/cv.pdf" class="btn" download>
            <i class="fas fa-download"></i> Download CV
          </a>
        </div>
        <div class="about-stats">
          <div class="stat-item" v-for="stat in stats" :key="stat.label">
            <div class="stat-number">{{ stat.number }}</div>
            <div class="stat-label">{{ stat.label }}</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'About',
  data() {
    return {
      stats: [
        { number: '10+', label: 'Proyek Selesai' },
        { number: '2+', label: 'Tahun Pengalaman' },
        { number: '5+', label: 'Klien Puas' },
        { number: '3', label: 'Sertifikasi' }
      ]
    }
  }
}
</script>

<style scoped>
.about {
  background: white;
}

.about-content {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 4rem;
  align-items: start;
}

.about-text p {
  margin-bottom: 1.5rem;
  font-size: 1.1rem;
  line-height: 1.8;
  color: #555;
}

.about-info {
  margin: 2rem 0;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.info-item {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.info-item strong {
  color: #2c3e50;
  font-weight: 600;
}

.info-item span {
  color: #666;
}

.about-stats {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
}

.stat-item {
  text-align: center;
  padding: 2rem;
  background: #f8f9fa;
  border-radius: 10px;
  transition: transform 0.3s ease;
}

.stat-item:hover {
  transform: translateY(-5px);
}

.stat-number {
  font-size: 2.5rem;
  font-weight: 700;
  color: #3498db;
  margin-bottom: 0.5rem;
}

.stat-label {
  color: #666;
  font-weight: 500;
}

/* Responsive */
@media (max-width: 768px) {
  .about-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .about-info {
    grid-template-columns: 1fr;
  }

  .about-stats {
    grid-template-columns: 1fr;
    gap: 1rem;
  }

  .stat-item {
    padding: 1.5rem;
  }
}
</style>