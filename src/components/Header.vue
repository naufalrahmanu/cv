<template>
  <header class="header">
    <nav class="nav">
      <div class="container">
        <div class="nav-content">
          <div class="logo">
            <h2>Portfolio</h2>
          </div>
          <ul class="nav-links">
            <li><a href="#about" @click="scrollToSection">Tentang</a></li>
            <li><a href="#skills" @click="scrollToSection">Keahlian</a></li>
            <li><a href="#portfolio" @click="scrollToSection">Portfolio</a></li>
            <li><a href="#contact" @click="scrollToSection">Kontak</a></li>
          </ul>
          <div class="hamburger" @click="toggleMenu">
            <span></span>
            <span></span>
            <span></span>
          </div>
        </div>
      </div>
    </nav>

    <div class="hero">
      <div class="container">
        <div class="hero-content">
          <div class="hero-text">
            <h1>Hai, Saya <span class="highlight">Nama Anda</span></h1>
            <h2>Web Developer</h2>
            <p>Saya seorang developer yang passionate dalam membangun website dan aplikasi yang menarik dan fungsional.</p>
            <div class="hero-buttons">
              <a href="#portfolio" class="btn btn-primary" @click="scrollToSection">Lihat Portfolio</a>
              <a href="#contact" class="btn btn-secondary" @click="scrollToSection">Hubungi Saya</a>
            </div>
          </div>
          <div class="hero-image">
            <div class="image-placeholder">
              <i class="fas fa-user"></i>
            </div>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  methods: {
    scrollToSection(event) {
      event.preventDefault();
      const targetId = event.target.getAttribute('href').substring(1);
      const targetElement = document.getElementById(targetId);
      if (targetElement) {
        targetElement.scrollIntoView({ behavior: 'smooth' });
      }
      this.toggleMenu(false);
    },
    toggleMenu(forceClose = null) {
      const navLinks = document.querySelector('.nav-links');
      if (forceClose === false || (forceClose === null && navLinks.classList.contains('active'))) {
        navLinks.classList.remove('active');
      } else {
        navLinks.classList.toggle('active');
      }
    }
  }
}
</script>

<style scoped>
.header {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  min-height: 100vh;
  position: relative;
}

.nav {
  position: fixed;
  top: 0;
  width: 100%;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  z-index: 1000;
  padding: 1rem 0;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.nav-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo h2 {
  color: #2c3e50;
  font-weight: 600;
}

.nav-links {
  display: flex;
  list-style: none;
  gap: 2rem;
}

.nav-links a {
  text-decoration: none;
  color: #2c3e50;
  font-weight: 500;
  transition: color 0.3s ease;
  cursor: pointer;
}

.nav-links a:hover {
  color: #3498db;
}

.hamburger {
  display: none;
  flex-direction: column;
  cursor: pointer;
}

.hamburger span {
  width: 25px;
  height: 3px;
  background: #2c3e50;
  margin: 3px 0;
  transition: 0.3s;
}

.hero {
  padding-top: 100px;
  display: flex;
  align-items: center;
  min-height: 100vh;
}

.hero-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
}

.hero-text h1 {
  font-size: 3.5rem;
  margin-bottom: 1rem;
  font-weight: 700;
}

.highlight {
  color: #f39c12;
}

.hero-text h2 {
  font-size: 2rem;
  margin-bottom: 1.5rem;
  font-weight: 400;
  opacity: 0.9;
}

.hero-text p {
  font-size: 1.2rem;
  margin-bottom: 2rem;
  opacity: 0.8;
  line-height: 1.8;
}

.hero-buttons {
  display: flex;
  gap: 1rem;
}

.btn-primary {
  background: #f39c12;
}

.btn-primary:hover {
  background: #e67e22;
}

.btn-secondary {
  background: transparent;
  border: 2px solid white;
}

.btn-secondary:hover {
  background: white;
  color: #333;
}

.hero-image {
  display: flex;
  justify-content: center;
}

.image-placeholder {
  width: 300px;
  height: 300px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 8rem;
  backdrop-filter: blur(10px);
  border: 3px solid rgba(255, 255, 255, 0.2);
}

/* Responsive */
@media (max-width: 768px) {
  .hamburger {
    display: flex;
  }

  .nav-links {
    position: fixed;
    top: 70px;
    left: -100%;
    width: 100%;
    background: white;
    flex-direction: column;
    text-align: center;
    transition: 0.3s;
    box-shadow: 0 10px 27px rgba(0, 0, 0, 0.05);
    padding: 2rem 0;
  }

  .nav-links.active {
    left: 0;
  }

  .hero-content {
    grid-template-columns: 1fr;
    text-align: center;
    gap: 2rem;
  }

  .hero-text h1 {
    font-size: 2.5rem;
  }

  .hero-text h2 {
    font-size: 1.5rem;
  }

  .hero-buttons {
    justify-content: center;
    flex-wrap: wrap;
  }

  .image-placeholder {
    width: 200px;
    height: 200px;
    font-size: 5rem;
  }
}
</style>