<template>
  <section id="portfolio" class="section portfolio">
    <div class="container">
      <h2 class="section-title">Portfolio</h2>
      <div class="portfolio-filters">
        <button 
          v-for="filter in filters" 
          :key="filter" 
          :class="['filter-btn', { active: activeFilter === filter }]"
          @click="setFilter(filter)"
        >
          {{ filter }}
        </button>
      </div>
      <div class="portfolio-grid">
        <div 
          v-for="project in filteredProjects" 
          :key="project.id" 
          class="portfolio-item"
          @click="openModal(project)"
        >
          <div class="portfolio-image">
            <img :src="project.image" :alt="project.title">
            <div class="portfolio-overlay">
              <div class="portfolio-actions">
                <button class="action-btn" @click.stop="openModal(project)">
                  <i class="fas fa-eye"></i>
                </button>
                <a :href="project.demo" class="action-btn" target="_blank" @click.stop>
                  <i class="fas fa-external-link-alt"></i>
                </a>
              </div>
            </div>
          </div>
          <div class="portfolio-info">
            <h3>{{ project.title }}</h3>
            <p>{{ project.description }}</p>
            <div class="portfolio-tags">
              <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal -->
    <div v-if="selectedProject" class="modal" :class="{ active: showModal }" @click="closeModal">
      <div class="modal-content" @click.stop>
        <button class="modal-close" @click="closeModal">
          <i class="fas fa-times"></i>
        </button>
        <div class="modal-body">
          <div class="modal-image">
            <img :src="selectedProject.image" :alt="selectedProject.title">
          </div>
          <div class="modal-info">
            <h2>{{ selectedProject.title }}</h2>
            <p>{{ selectedProject.fullDescription }}</p>
            <div class="modal-tags">
              <span v-for="tag in selectedProject.tags" :key="tag" class="tag">{{ tag }}</span>
            </div>
            <div class="modal-links">
              <a :href="selectedProject.demo" class="btn" target="_blank">
                <i class="fas fa-external-link-alt"></i> Live Demo
              </a>
              <a :href="selectedProject.github" class="btn btn-secondary" target="_blank">
                <i class="fab fa-github"></i> Source Code
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Portfolio',
  data() {
    return {
      activeFilter: 'All',
      filters: ['All', 'Web', 'Mobile', 'Design'],
      showModal: false,
      selectedProject: null,
      projects: [
        {
          id: 1,
          title: 'E-Commerce Website',
          description: 'Website e-commerce modern dengan Vue.js',
          fullDescription: 'Website e-commerce lengkap dengan sistem cart, checkout, dan payment integration. Dibangun menggunakan Vue.js, Vuex, dan Firebase.',
          image: '/api/placeholder/600/400',
          tags: ['Vue.js', 'Firebase', 'CSS'],
          category: 'Web',
          demo: 'https://demo.example.com',
          github: 'https://github.com/username/project1'
        },
        {
          id: 2,
          title: 'Task Management App',
          description: 'Aplikasi manajemen tugas dengan drag & drop',
          fullDescription: 'Aplikasi untuk mengelola tugas dengan fitur drag & drop, real-time updates, dan team collaboration.',
          image: '/api/placeholder/600/400',
          tags: ['React', 'Node.js', 'MongoDB'],
          category: 'Web',
          demo: 'https://demo.example.com',
          github: 'https://github.com/username/project2'
        },
        {
          id: 3,
          title: 'Mobile Weather App',
          description: 'Aplikasi cuaca untuk mobile',
          fullDescription: 'Aplikasi cuaca dengan GPS integration, weather forecasts, dan beautiful UI design.',
          image: '/api/placeholder/600/400',
          tags: ['React Native', 'API', 'JavaScript'],
          category: 'Mobile',
          demo: 'https://demo.example.com',
          github: 'https://github.com/username/project3'
        },
        {
          id: 4,
          title: 'UI/UX Design System',
          description: 'Design system untuk web application',
          fullDescription: 'Comprehensive design system dengan components, patterns, dan design tokens untuk konsistensi UI.',
          image: '/api/placeholder/600/400',
          tags: ['Figma', 'Design', 'UI/UX'],
          category: 'Design',
          demo: 'https://demo.example.com',
          github: 'https://github.com/username/project4'
        }
      ]
    }
  },
  computed: {
    filteredProjects() {
      if (this.activeFilter === 'All') {
        return this.projects
      }
      return this.projects.filter(project => project.category === this.activeFilter)
    }
  },
  methods: {
    setFilter(filter) {
      this.activeFilter = filter
    },
    openModal(project) {
      this.selectedProject = project
      this.showModal = true
      document.body.style.overflow = 'hidden'
    },
    closeModal() {
      this.showModal = false
      this.selectedProject = null
      document.body.style.overflow = 'auto'
    }
  }
}
</script>

<style scoped>
.portfolio {
  background: white;
}

.portfolio-filters {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 3rem;
  flex-wrap: wrap;
}

.filter-btn {
  padding: 10px 20px;
  background: #f8f9fa;
  border: none;
  border-radius: 25px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-weight: 500;
}

.filter-btn.active,
.filter-btn:hover {
  background: #3498db;
  color: white;
}

.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.portfolio-item {
  background: white;
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  cursor: pointer;
}

.portfolio-item:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
}

.portfolio-image {
  position: relative;
  overflow: hidden;
  height: 250px;
}

.portfolio-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.portfolio-item:hover .portfolio-image img {
  transform: scale(1.1);
}

.portfolio-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(52, 152, 219, 0.9);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.portfolio-item:hover .portfolio-overlay {
  opacity: 1;
}

.portfolio-actions {
  display: flex;
  gap: 1rem;
}

.action-btn {
  width: 50px;
  height: 50px;
  background: white;
  border: none;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #3498db;
  text-decoration: none;
  transition: all 0.3s ease;
  cursor: pointer;
}

.action-btn:hover {
  transform: scale(1.1);
  background: #f8f9fa;
}

.portfolio-info {
  padding: 1.5rem;
}

.portfolio-info h3 {
  font-size: 1.3rem;
  margin-bottom: 0.5rem;
  color: #2c3e50;
}

.portfolio-info p {
  color: #666;
  margin-bottom: 1rem;
  line-height: 1.6;
}

.portfolio-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tag {
  background: #e3f2fd;
  color: #1976d2;
  padding: 4px 12px;
  border-radius: 15px;
  font-size: 0.8rem;
  font-weight: 500;
}

/* Modal Styles */
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2000;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
  padding: 20px;
}

.modal.active {
  opacity: 1;
  visibility: visible;
}

.modal-content {
  background: white;
  border-radius: 15px;
  max-width: 900px;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
  transform: scale(0.7);
  transition: transform 0.3s ease;
}

.modal.active .modal-content {
  transform: scale(1);
}

.modal-close {
  position: absolute;
  top: 15px;
  right: 15px;
  background: none;
  border: none;
  font-size: 1.5rem;
  color: #666;
  cursor: pointer;
  z-index: 1;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.3s ease;
}

.modal-close:hover {
  background: #f8f9fa;
}

.modal-body {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0;
}

.modal-image {
  height: 400px;
}

.modal-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 15px 0 0 15px;
}

.modal-info {
  padding: 2rem;
}

.modal-info h2 {
  font-size: 2rem;
  margin-bottom: 1rem;
  color: #2c3e50;
}

.modal-info p {
  color: #666;
  line-height: 1.8;
  margin-bottom: 1.5rem;
}

.modal-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 2rem;
}

.modal-links {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.btn-secondary {
  background: #6c757d;
}

.btn-secondary:hover {
  background: #5a6268;
}

/* Responsive */
@media (max-width: 768px) {
  .portfolio-grid {
    grid-template-columns: 1fr;
  }

  .modal-body {
    grid-template-columns: 1fr;
  }

  .modal-image {
    height: 250px;
    border-radius: 15px 15px 0 0;
  }

  .modal-image img {
    border-radius: 15px 15px 0 0;
  }

  .modal-info {
    padding: 1.5rem;
  }

  .modal-links {
    flex-direction: column;
  }

  .portfolio-filters {
    gap: 0.5rem;
  }

  .filter-btn {
    padding: 8px 16px;
    font-size: 0.9rem;
  }
}
</style>