<template>
  <div class="projects">
    <div class="container">
      <h1 class="section-title">My Projects</h1>
      
      <div v-if="loading" class="loading">
        <p>Loading projects...</p>
      </div>

      <div v-else-if="error" class="error">
        <p>Error loading projects: {{ error }}</p>
        <button @click="fetchProjects" class="btn">Try Again</button>
      </div>

      <div v-else class="projects-grid">
        <div 
          v-for="project in projects" 
          :key="project.id" 
          class="project-card"
          @click="goToProject(project.id)"
        >
          <div class="project-image">
            <div class="image-placeholder">
              <span>📁</span>
            </div>
          </div>
          <div class="project-content">
            <h2>{{ project.name }}</h2>
            <p class="project-intro">{{ project.introduction }}</p>
            <div class="project-tech">
              <span 
                v-for="tech in project.technologies.slice(0, 4)" 
                :key="tech" 
                class="tech-tag"
              >
                {{ tech }}
              </span>
              <span v-if="project.technologies.length > 4" class="tech-tag">
                +{{ project.technologies.length - 4 }}
              </span>
            </div>
            <div class="project-links">
              <a 
                :href="project.githubUrl" 
                target="_blank" 
                rel="noopener noreferrer"
                @click.stop
                class="project-link"
              >
                GitHub →
              </a>
              <a 
                v-if="project.demoUrl"
                :href="project.demoUrl" 
                target="_blank" 
                rel="noopener noreferrer"
                @click.stop
                class="project-link"
              >
                Live Demo →
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const projects = ref([])
const loading = ref(true)
const error = ref(null)

const fetchProjects = async () => {
  try {
    loading.value = true
    error.value = null
    const response = await fetch('/data/projects.json')
    if (!response.ok) {
      throw new Error('Failed to fetch projects')
    }
    const data = await response.json()
    projects.value = data
  } catch (err) {
    error.value = err.message
    console.error('Error fetching projects:', err)
  } finally {
    loading.value = false
  }
}

const goToProject = (id) => {
  router.push(`/projects/${id}`)
}

onMounted(() => {
  fetchProjects()
})
</script>

<style scoped>
.projects {
  padding: 2rem 0;
  min-height: calc(100vh - 200px);
}

.loading,
.error {
  text-align: center;
  padding: 3rem;
  font-size: 1.2rem;
  color: var(--text-light);
}

.error {
  color: #ef4444;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

.project-card {
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: var(--shadow);
  transition: all 0.3s ease;
  cursor: pointer;
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-hover);
  border-color: var(--primary-color);
  background: var(--bg-card-hover);
}

.project-image {
  width: 100%;
  height: 200px;
  background: var(--primary-color);
  display: flex;
  align-items: center;
  justify-content: center;
}

.image-placeholder {
  font-size: 4rem;
  color: white;
  opacity: 0.8;
}

.project-content {
  padding: 1.5rem;
}

.project-content h2 {
  color: var(--primary-color);
  margin-bottom: 1rem;
  font-size: 1.5rem;
}

.project-intro {
  color: var(--text-light);
  line-height: 1.6;
  margin-bottom: 1rem;
}

.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.tech-tag {
  padding: 0.25rem 0.75rem;
  background: rgba(6, 182, 212, 0.1);
  color: var(--primary-color);
  border: 1px solid rgba(6, 182, 212, 0.3);
  border-radius: 15px;
  font-size: 0.85rem;
  font-weight: 500;
  transition: all 0.2s ease;
}

.tech-tag:hover {
  background: rgba(6, 182, 212, 0.2);
  border-color: var(--primary-color);
}

.project-links {
  display: flex;
  gap: 1rem;
  margin-top: 1rem;
}

.project-link {
  color: var(--primary-color);
  text-decoration: none;
  font-weight: 500;
  transition: opacity 0.3s;
}

.project-link:hover {
  opacity: 0.8;
  text-decoration: underline;
}

@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }

  .project-content {
    padding: 1rem;
  }
}
</style>

