<template>
  <div class="home">
    <section class="hero">
      <div class="container">
        <div class="hero-content">
          <div class="avatar-container">
            <div class="avatar">
              <span class="avatar-initials">🐑</span>
            </div>
          </div>
          <h1 class="hero-title">Welcome to My Portfolio</h1>
          <p class="hero-subtitle">Hello! I'm a passionate developer who loves building amazing web experiences.</p>
          <p class="hero-description">
            I'm dedicated to creating innovative solutions and learning new technologies. 
            This website showcases my projects, skills, and thoughts on web development.
          </p>
          <div class="hero-links">
            <router-link to="/projects" class="btn">View Projects</router-link>
            <router-link to="/blog" class="btn btn-secondary">Read Blog</router-link>
            <router-link to="/about" class="btn btn-secondary">Learn More</router-link>
          </div>
        </div>
      </div>
    </section>

    <section class="quick-links">
      <div class="container">
        <h2 class="section-title">Quick Navigation</h2>
        <div class="links-grid">
          <router-link to="/about" class="link-card">
            <h3>About Me</h3>
            <p>Learn more about my background, interests, and aspirations</p>
          </router-link>
          <router-link to="/skills" class="link-card">
            <h3>Skills & Resume</h3>
            <p>View my technical skills and educational background</p>
          </router-link>
          <router-link to="/projects" class="link-card">
            <h3>Projects</h3>
            <p>Explore my portfolio of projects and GitHub repositories</p>
          </router-link>
          <router-link to="/blog" class="link-card">
            <h3>Blog</h3>
            <p>Read my thoughts and experiences in web development</p>
          </router-link>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
</script>

<style scoped>
.home {
  min-height: calc(100vh - 200px);
}

.hero {
  padding: 4rem 0;
  background: linear-gradient(135deg, rgba(6, 182, 212, 0.1) 0%, rgba(15, 23, 42, 0.5) 100%);
  border-bottom: 1px solid var(--border-color);
  color: var(--text-color);
  text-align: center;
  position: relative;
  overflow: hidden;
}

.hero::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: radial-gradient(circle at 50% 50%, rgba(6, 182, 212, 0.1) 0%, transparent 70%);
  pointer-events: none;
}

.hero-content {
  max-width: 800px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
}

.avatar-container {
  margin-bottom: 2rem;
  position: relative;
  z-index: 1;
}

.avatar {
  width: 150px;
  height: 150px;
  margin: 0 auto;
  border-radius: 50%;
  overflow: hidden;
  border: 4px solid var(--primary-color);
  box-shadow: 0 0 30px rgba(6, 182, 212, 0.5), var(--shadow);
  background: var(--bg-secondary);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
}

.avatar:hover {
  border-color: var(--secondary-color);
  box-shadow: 0 0 40px rgba(6, 182, 212, 0.7), var(--shadow-hover);
  transform: scale(1.05);
}

.avatar-initials {
  font-size: 3rem;
  font-weight: bold;
  color: var(--primary-color);
  text-shadow: 0 0 20px rgba(6, 182, 212, 0.5);
}

.hero-title {
  font-size: 3rem;
  margin-bottom: 1rem;
  font-weight: bold;
  color: var(--text-color);
  position: relative;
  z-index: 1;
}

.hero-subtitle {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: var(--text-light);
  position: relative;
  z-index: 1;
}

.hero-description {
  font-size: 1.1rem;
  margin-bottom: 2rem;
  color: var(--text-light);
  line-height: 1.8;
  position: relative;
  z-index: 1;
}

.hero-links {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
  position: relative;
  z-index: 1;
}

.quick-links {
  padding: 4rem 0;
}

.links-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

.link-card {
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  padding: 2rem;
  border-radius: 12px;
  box-shadow: var(--shadow);
  text-decoration: none;
  color: var(--text-color);
  transition: all 0.3s ease;
}

.link-card:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-hover);
  border-color: var(--primary-color);
  background: var(--bg-card-hover);
}

.link-card:hover h3 {
  color: var(--primary-color);
}

.link-card h3 {
  color: var(--text-color);
  margin-bottom: 1rem;
  font-size: 1.5rem;
  transition: color 0.3s ease;
}

.link-card p {
  color: var(--text-light);
  line-height: 1.6;
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 2rem;
  }

  .hero-subtitle {
    font-size: 1.2rem;
  }

  .hero-description {
    font-size: 1rem;
  }

  .hero-links {
    flex-direction: column;
    align-items: center;
  }

  .hero-links .btn {
    width: 100%;
    max-width: 300px;
  }

  .links-grid {
    grid-template-columns: 1fr;
  }

  .quick-links {
    padding: 2rem 0;
  }
}
</style>

