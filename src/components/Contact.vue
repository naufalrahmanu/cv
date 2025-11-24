<template>
  <section id="contact" class="section contact">
    <div class="container">
      <h2 class="section-title">Hubungi Saya</h2>
      <div class="contact-content">
        <div class="contact-info">
          <h3>Mari Berkolaborasi!</h3>
          <p>
            Tertarik untuk bekerja bersama? Silakan hubungi saya melalui form di samping 
            atau melalui kontak di bawah ini.
          </p>
          <div class="contact-items">
            <div class="contact-item">
              <div class="contact-icon">
                <i class="fas fa-envelope"></i>
              </div>
              <div class="contact-details">
                <h4>Email</h4>
                <span>email@example.com</span>
              </div>
            </div>
            <div class="contact-item">
              <div class="contact-icon">
                <i class="fas fa-phone"></i>
              </div>
              <div class="contact-details">
                <h4>Telepon</h4>
                <span>+62 812-3456-7890</span>
              </div>
            </div>
            <div class="contact-item">
              <div class="contact-icon">
                <i class="fas fa-map-marker-alt"></i>
              </div>
              <div class="contact-details">
                <h4>Lokasi</h4>
                <span>Kota, Negara</span>
              </div>
            </div>
          </div>
          <div class="social-links">
            <a href="#" class="social-link">
              <i class="fab fa-linkedin"></i>
            </a>
            <a href="#" class="social-link">
              <i class="fab fa-github"></i>
            </a>
            <a href="#" class="social-link">
              <i class="fab fa-instagram"></i>
            </a>
            <a href="#" class="social-link">
              <i class="fab fa-twitter"></i>
            </a>
          </div>
        </div>
        <form class="contact-form" @submit.prevent="submitForm">
          <div class="form-group">
            <label for="name">Nama Lengkap</label>
            <input 
              type="text" 
              id="name" 
              v-model="form.name"
              required
              placeholder="Masukkan nama lengkap"
            >
          </div>
          <div class="form-group">
            <label for="email">Email</label>
            <input 
              type="email" 
              id="email" 
              v-model="form.email"
              required
              placeholder="Masukkan alamat email"
            >
          </div>
          <div class="form-group">
            <label for="subject">Subjek</label>
            <input 
              type="text" 
              id="subject" 
              v-model="form.subject"
              required
              placeholder="Masukkan subjek pesan"
            >
          </div>
          <div class="form-group">
            <label for="message">Pesan</label>
            <textarea 
              id="message" 
              rows="5"
              v-model="form.message"
              required
              placeholder="Tulis pesan Anda di sini..."
            ></textarea>
          </div>
          <button type="submit" class="btn btn-submit" :disabled="loading">
            <span v-if="loading">
              <i class="fas fa-spinner fa-spin"></i> Mengirim...
            </span>
            <span v-else>
              <i class="fas fa-paper-plane"></i> Kirim Pesan
            </span>
          </button>
        </form>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Contact',
  data() {
    return {
      loading: false,
      form: {
        name: '',
        email: '',
        subject: '',
        message: ''
      }
    }
  },
  methods: {
    async submitForm() {
      this.loading = true
      
      // Simulasi pengiriman form
      await new Promise(resolve => setTimeout(resolve, 2000))
      
      // Reset form
      this.form = {
        name: '',
        email: '',
        subject: '',
        message: ''
      }
      
      this.loading = false
      alert('Pesan berhasil dikirim! Saya akan membalasnya segera.')
    }
  }
}
</script>

<style scoped>
.contact {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
}

.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: start;
}

.contact-info h3 {
  font-size: 2rem;
  margin-bottom: 1rem;
}

.contact-info p {
  font-size: 1.1rem;
  line-height: 1.8;
  margin-bottom: 2rem;
  opacity: 0.9;
}

.contact-items {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  margin-bottom: 2rem;
}

.contact-item {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.contact-icon {
  width: 50px;
  height: 50px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2rem;
  backdrop-filter: blur(10px);
}

.contact-details h4 {
  font-size: 1.1rem;
  margin-bottom: 0.3rem;
  font-weight: 600;
}

.contact-details span {
  opacity: 0.8;
}

.social-links {
  display: flex;
  gap: 1rem;
}

.social-link {
  width: 45px;
  height: 45px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  color: white;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.social-link:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-3px);
}

.contact-form {
  background: rgba(255, 255, 255, 0.1);
  padding: 2rem;
  border-radius: 15px;
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: 500;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 12px 15px;
  background: rgba(255, 255, 255, 0.9);
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  transition: all 0.3s ease;
  font-family: inherit;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  background: white;
  box-shadow: 0 0 0 3px rgba(255, 255, 255, 0.3);
}

.form-group textarea {
  resize: vertical;
  min-height: 120px;
}

.btn-submit {
  width: 100%;
  background: #f39c12;
  font-size: 1.1rem;
  padding: 15px;
}

.btn-submit:hover {
  background: #e67e22;
}

.btn-submit:disabled {
  background: #95a5a6;
  cursor: not-allowed;
  transform: none;
}

/* Responsive */
@media (max-width: 768px) {
  .contact-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .contact-form {
    padding: 1.5rem;
  }

  .contact-info h3 {
    font-size: 1.5rem;
  }
}
</style>