<template>
  <section id="skills" class="section skills">
    <div class="container">
      <h2 class="section-title">Keahlian</h2>
      <div class="skills-content">
        <div class="skills-category" v-for="category in skillCategories" :key="category.name">
          <h3 class="category-title">{{ category.name }}</h3>
          <div class="skills-list">
            <div class="skill-item" v-for="skill in category.skills" :key="skill.name">
              <div class="skill-header">
                <span class="skill-name">{{ skill.name }}</span>
                <span class="skill-percentage">{{ skill.percentage }}%</span>
              </div>
              <div class="skill-bar">
                <div 
                  class="skill-progress" 
                  :style="{ width: skill.percentage + '%' }"
                  :data-percentage="skill.percentage"
                ></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      skillCategories: [
        {
          name: 'Frontend Development',
          skills: [
            { name: 'Vue.js', percentage: 90 },
            { name: 'React', percentage: 85 },
            { name: 'JavaScript', percentage: 88 },
            { name: 'HTML/CSS', percentage: 95 }
          ]
        },
        {
          name: 'Backend Development',
          skills: [
            { name: 'Node.js', percentage: 80 },
            { name: 'Express.js', percentage: 75 },
            { name: 'PHP', percentage: 70 },
            { name: 'MySQL', percentage: 85 }
          ]
        },
        {
          name: 'Tools & Lainnya',
          skills: [
            { name: 'Git', percentage: 88 },
            { name: 'Docker', percentage: 65 },
            { name: 'AWS', percentage: 60 },
            { name: 'Figma', percentage: 75 }
          ]
        }
      ]
    }
  }
}
</script>

<style scoped>
.skills {
  background: #f8f9fa;
}

.skills-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 3rem;
}

.category-title {
  font-size: 1.5rem;
  color: #2c3e50;
  margin-bottom: 2rem;
  text-align: center;
  position: relative;
}

.category-title::after {
  content: '';
  position: absolute;
  bottom: -8px;
  left: 50%;
  transform: translateX(-50%);
  width: 40px;
  height: 2px;
  background: #3498db;
}

.skills-list {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.skill-item {
  background: white;
  padding: 1.5rem;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.skill-item:hover {
  transform: translateY(-3px);
}

.skill-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.8rem;
}

.skill-name {
  font-weight: 600;
  color: #2c3e50;
}

.skill-percentage {
  font-weight: 600;
  color: #3498db;
}

.skill-bar {
  height: 8px;
  background: #e9ecef;
  border-radius: 4px;
  overflow: hidden;
}

.skill-progress {
  height: 100%;
  background: linear-gradient(90deg, #3498db, #2980b9);
  border-radius: 4px;
  transition: width 1.5s ease-in-out;
  position: relative;
}

.skill-progress::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
  animation: shimmer 2s infinite;
}

@keyframes shimmer {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(100%); }
}

/* Responsive */
@media (max-width: 768px) {
  .skills-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .skill-item {
    padding: 1rem;
  }
}
</style>