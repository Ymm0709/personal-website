<template>
  <div class="links">
    <div class="container">
      <h1 class="section-title">Useful Links</h1>
      
      <section class="links-section">
        <h2>Friends' Websites</h2>
        <div class="links-grid">
          <div 
            v-for="link in friendLinks" 
            :key="link.id" 
            class="link-card"
          >
            <div class="link-icon">{{ link.icon }}</div>
            <h3>{{ link.title }}</h3>
            <p>{{ link.description }}</p>
            <a :href="link.url" target="_blank" rel="noopener noreferrer" class="link-button">
              Visit Site →
            </a>
          </div>
        </div>
      </section>

      <section class="links-section">
        <h2>Learning Resources</h2>
        <div class="links-grid">
          <div 
            v-for="link in learningResources" 
            :key="link.id" 
            class="link-card"
          >
            <div class="link-icon">{{ link.icon }}</div>
            <h3>{{ link.title }}</h3>
            <p>{{ link.description }}</p>
            <a :href="link.url" target="_blank" rel="noopener noreferrer" class="link-button">
              Visit Site →
            </a>
          </div>
        </div>
      </section>

      <section class="links-section">
        <h2>Developers I Admire</h2>
        <div class="links-grid">
          <div 
            v-for="link in developerLinks" 
            :key="link.id" 
            class="link-card"
          >
            <div class="link-icon">{{ link.icon }}</div>
            <h3>{{ link.title }}</h3>
            <p>{{ link.description }}</p>
            <a :href="link.url" target="_blank" rel="noopener noreferrer" class="link-button">
              Visit Profile →
            </a>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const friendLinks = ref([
  {
    id: 1,
    title: 'Friend\'s Portfolio',
    description: 'A fellow developer\'s amazing portfolio showcasing their projects and skills.',
    url: 'https://example.com',
    icon: '👨‍💻'
  },
  {
    id: 2,
    title: 'Colleague\'s Blog',
    description: 'Interesting tech blog with insightful articles about web development.',
    url: 'https://example.com',
    icon: '📝'
  }
])

const learningResources = ref([
  {
    id: 1,
    title: 'MDN Web Docs',
    description: 'Comprehensive documentation for web technologies including HTML, CSS, and JavaScript.',
    url: 'https://developer.mozilla.org',
    icon: '📚'
  },
  {
    id: 2,
    title: 'Vue.js Official Docs',
    description: 'Official documentation and guides for Vue.js framework.',
    url: 'https://vuejs.org',
    icon: '🟢'
  },
  {
    id: 3,
    title: 'freeCodeCamp',
    description: 'Free online coding bootcamp with interactive lessons and projects.',
    url: 'https://www.freecodecamp.org',
    icon: '🎓'
  },
  {
    id: 4,
    title: 'Stack Overflow',
    description: 'Q&A platform for programmers to ask questions and share knowledge.',
    url: 'https://stackoverflow.com',
    icon: '💬'
  }
])

const developerLinks = ref([
  {
    id: 1,
    title: 'Evan You',
    description: 'Creator of Vue.js and Vite. Inspiring open-source contributor.',
    url: 'https://github.com/yyx990803',
    icon: '⭐'
  },
  {
    id: 2,
    title: 'Dan Abramov',
    description: 'Co-author of Redux and Create React App. Great educator in React community.',
    url: 'https://github.com/gaearon',
    icon: '⚛️'
  },
  {
    id: 3,
    title: 'Addy Osmani',
    description: 'Engineering manager and author. Known for web performance optimization.',
    url: 'https://github.com/addyosmani',
    icon: '🚀'
  }
])
</script>

<style scoped>
.links {
  padding: 2rem 0;
  min-height: calc(100vh - 200px);
}

.links-section {
  margin-bottom: 4rem;
}

.links-section h2 {
  color: var(--primary-color);
  margin-bottom: 2rem;
  font-size: 2rem;
  text-align: center;
}

.links-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
}

.link-card {
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  padding: 2rem;
  border-radius: 12px;
  box-shadow: var(--shadow);
  transition: all 0.3s ease;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.link-card:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-hover);
  border-color: var(--primary-color);
  background: var(--bg-card-hover);
}

.link-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.link-card h3 {
  color: var(--primary-color);
  margin-bottom: 1rem;
  font-size: 1.5rem;
}

.link-card p {
  color: var(--text-light);
  line-height: 1.6;
  margin-bottom: 1.5rem;
  flex-grow: 1;
}

.link-button {
  display: inline-block;
  padding: 0.75rem 1.5rem;
  background: var(--primary-color);
  color: white;
  text-decoration: none;
  border-radius: 5px;
  transition: background-color 0.2s;
  font-weight: 500;
}

.link-button:hover {
  background: var(--primary-hover);
}

@media (max-width: 768px) {
  .links-grid {
    grid-template-columns: 1fr;
  }

  .link-card {
    padding: 1.5rem;
  }
}
</style>

