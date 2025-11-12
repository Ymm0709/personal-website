<template>
  <div class="project-detail">
    <div class="container">
      <div v-if="loading" class="loading">
        <p>Loading project...</p>
      </div>

      <div v-else-if="error" class="error">
        <p>Error loading project: {{ error }}</p>
        <router-link to="/projects" class="btn">Back to Projects</router-link>
      </div>

      <div v-else-if="project" class="project-detail-content">
        <button @click="goBack" class="back-button">← Back to Projects</button>
        
        <h1 class="project-title">{{ project.name }}</h1>
        
        <div class="project-header">
          <p class="project-intro">{{ project.introduction }}</p>
        </div>

        <div class="project-screenshots" v-if="project.screenshots">
          <h2>Screenshots</h2>
          <div class="screenshots-grid">
            <div 
              v-for="(screenshot, index) in project.screenshots" 
              :key="index" 
              class="screenshot-placeholder"
            >
              <span>Image {{ index + 1 }}</span>
            </div>
          </div>
        </div>

        <div class="project-section">
          <h2>Description</h2>
          <p class="project-description">{{ project.description }}</p>
        </div>

        <div class="project-section">
          <h2>Technologies Used</h2>
          <div class="tech-list">
            <span 
              v-for="tech in project.technologies" 
              :key="tech" 
              class="tech-badge"
            >
              {{ tech }}
            </span>
          </div>
        </div>

        <div class="project-section">
          <h2>My Contribution</h2>
          <p>{{ project.contribution }}</p>
        </div>

        <div class="project-links-section">
          <h2>Links</h2>
          <div class="project-links">
            <a 
              :href="project.githubUrl" 
              target="_blank" 
              rel="noopener noreferrer"
              class="btn"
            >
              View on GitHub
            </a>
            <a 
              v-if="project.demoUrl"
              :href="project.demoUrl" 
              target="_blank" 
              rel="noopener noreferrer"
              class="btn btn-secondary"
            >
              Live Demo
            </a>
          </div>
        </div>
      </div>

      <div v-else class="not-found">
        <p>Project not found</p>
        <router-link to="/projects" class="btn">Back to Projects</router-link>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRouter, useRoute } from 'vue-router'

const router = useRouter()
const route = useRoute()
const project = ref(null)
const loading = ref(true)
const error = ref(null)

const fetchProject = async () => {
  try {
    loading.value = true
    error.value = null
    const response = await fetch('/data/projects.json')
    if (!response.ok) {
      throw new Error('Failed to fetch projects')
    }
    const projects = await response.json()
    const projectId = parseInt(route.params.id)
    const foundProject = projects.find(p => p.id === projectId)
    
    if (foundProject) {
      project.value = foundProject
    } else {
      error.value = 'Project not found'
    }
  } catch (err) {
    error.value = err.message
    console.error('Error fetching project:', err)
  } finally {
    loading.value = false
  }
}

const goBack = () => {
  router.push('/projects')
}

onMounted(() => {
  fetchProject()
})
</script>

<style scoped>
.project-detail {
  padding: 2rem 0;
  min-height: calc(100vh - 200px);
}

.loading,
.error,
.not-found {
  text-align: center;
  padding: 3rem;
  font-size: 1.2rem;
  color: var(--text-light);
}

.error,
.not-found {
  color: #ef4444;
}

.back-button {
  background: transparent;
  border: 2px solid var(--primary-color);
  color: var(--primary-color);
  padding: 0.5rem 1rem;
  border-radius: 5px;
  cursor: pointer;
  margin-bottom: 2rem;
  font-size: 1rem;
  transition: all 0.3s;
}

.back-button:hover {
  background: var(--primary-color);
  color: var(--bg-color);
  box-shadow: var(--shadow-glow);
}

.project-detail-content {
  max-width: 900px;
  margin: 0 auto;
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  padding: 3rem;
  box-shadow: var(--shadow);
}

.project-title {
  font-size: 2.5rem;
  color: var(--primary-color);
  margin-bottom: 1rem;
}

.project-header {
  margin-bottom: 2rem;
}

.project-intro {
  font-size: 1.2rem;
  color: var(--text-light);
  line-height: 1.8;
}

.project-section {
  margin-bottom: 3rem;
  padding: 2rem;
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  box-shadow: var(--shadow);
  transition: all 0.3s ease;
}

.project-section:hover {
  border-color: var(--border-light);
  box-shadow: var(--shadow-hover);
}

.project-section h2 {
  color: var(--primary-color);
  margin-bottom: 1rem;
  font-size: 1.8rem;
}

.project-description {
  line-height: 1.8;
  color: var(--text-light);
  font-size: 1.1rem;
}

.tech-list {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.tech-badge {
  padding: 0.5rem 1rem;
  background: rgba(6, 182, 212, 0.2);
  color: var(--primary-color);
  border: 1px solid var(--primary-color);
  border-radius: 20px;
  font-weight: 500;
  transition: all 0.2s ease;
}

.tech-badge:hover {
  background: var(--primary-color);
  color: var(--bg-color);
  box-shadow: 0 0 10px rgba(6, 182, 212, 0.5);
}

.project-screenshots {
  margin-bottom: 3rem;
}

.project-screenshots h2 {
  color: var(--primary-color);
  margin-bottom: 1rem;
  font-size: 1.8rem;
}

.screenshots-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
}

.screenshot-placeholder {
  width: 100%;
  height: 200px;
  background: var(--bg-secondary);
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--text-light);
  font-weight: 500;
}

.project-links-section {
  margin-bottom: 2rem;
  padding: 2rem;
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  box-shadow: var(--shadow);
  transition: all 0.3s ease;
}

.project-links-section:hover {
  border-color: var(--border-light);
  box-shadow: var(--shadow-hover);
}

.project-links-section h2 {
  color: var(--primary-color);
  margin-bottom: 1rem;
  font-size: 1.8rem;
}

.project-links {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

@media (max-width: 768px) {
  .project-title {
    font-size: 2rem;
  }

  .project-section {
    padding: 1.5rem;
  }

  .screenshots-grid {
    grid-template-columns: 1fr;
  }

  .project-links {
    flex-direction: column;
  }

  .project-links .btn {
    width: 100%;
  }
}
</style>

