<template>
  <div class="about">
    <div class="container">
      <h1 class="section-title">About Me</h1>
      
      <section class="about-section">
        <div class="about-content">
          <div class="about-text">
            <h2>My Story</h2>
            <p>
              Hello! I'm a passionate web developer with a love for creating beautiful and functional 
              digital experiences. My journey in web development started with curiosity about how 
              websites work, and it has evolved into a full-fledged passion for building innovative 
              solutions.
            </p>
            <p>
              I believe in continuous learning and staying updated with the latest technologies and 
              best practices in web development. Whether it's front-end frameworks, back-end systems, 
              or new design patterns, I'm always excited to explore and implement new ideas.
            </p>
          </div>
          <div class="about-image">
            <img src="/MyPhoto.png" alt="My Photo" class="profile-photo" />
          </div>
        </div>
      </section>

      <section class="interests-section">
        <h2>Academic Interests</h2>
        <div class="interests-grid">
          <div class="interest-card">
            <h3>Web Development</h3>
            <p>Building responsive and interactive web applications using modern frameworks and technologies.</p>
          </div>
          <div class="interest-card">
            <h3>User Experience</h3>
            <p>Creating intuitive and user-friendly interfaces that provide exceptional user experiences.</p>
          </div>
          <div class="interest-card">
            <h3>Software Engineering</h3>
            <p>Applying best practices in software design, architecture, and development methodologies.</p>
          </div>
          <div class="interest-card">
            <h3>Data Structures</h3>
            <p>Understanding and implementing efficient algorithms and data structures for optimal performance.</p>
          </div>
        </div>
      </section>

      <section class="passions-section">
        <h2>My Passions</h2>
        <ul class="passions-list">
          <li>💻 Coding and building projects</li>
          <li>📚 Reading tech blogs and documentation</li>
          <li>🎨 Designing user interfaces</li>
          <li>🚀 Learning new technologies</li>
          <li>🤝 Collaborating on open-source projects</li>
          <li>📝 Writing about web development</li>
        </ul>
      </section>

      <section class="goals-section">
        <h2>Personal Aspirations & Goals</h2>
        <div class="goals-content">
          <p>
            My primary goal is to become a full-stack developer capable of building end-to-end 
            solutions that solve real-world problems. I aspire to work on projects that make a 
            positive impact on people's lives.
          </p>
          <p>
            I'm also passionate about contributing to the developer community by sharing knowledge, 
            writing technical articles, and helping others learn and grow in their coding journey.
          </p>
          <p>
            In the long term, I hope to lead development teams and mentor junior developers, 
            fostering a culture of continuous learning and innovation.
          </p>
        </div>
      </section>
    </div>
  </div>
</template>

<script setup>
</script>

<style scoped>
.about {
  padding: 2rem 0;
  min-height: calc(100vh - 200px);
}

.about-section {
  margin-bottom: 3rem;
}

.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: center;
}

.about-text h2 {
  color: var(--primary-color);
  margin-bottom: 1rem;
  font-size: 2rem;
}

.about-text p {
  margin-bottom: 1rem;
  line-height: 1.8;
  color: var(--text-light);
}

.about-image {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}

.about-image::before {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  border-radius: 10px;
  background: radial-gradient(circle, rgba(6, 182, 212, 0.1) 0%, transparent 70%);
  pointer-events: none;
}

.profile-photo {
  width: 100%;
  max-width: 300px;
  height: auto;
  border-radius: 10px;
  border: 2px solid var(--border-color);
  box-shadow: var(--shadow);
  object-fit: cover;
  transition: all 0.3s ease;
  position: relative;
  z-index: 1;
}

.profile-photo:hover {
  transform: scale(1.05);
  box-shadow: var(--shadow-hover), 0 0 30px rgba(6, 182, 212, 0.3);
  border-color: var(--primary-color);
}

.interests-section,
.passions-section,
.goals-section {
  margin-bottom: 3rem;
  padding: 2rem;
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  box-shadow: var(--shadow);
  transition: all 0.3s ease;
}

.interests-section:hover,
.passions-section:hover,
.goals-section:hover {
  border-color: var(--border-light);
  box-shadow: var(--shadow-hover);
}

.interests-section h2,
.passions-section h2,
.goals-section h2 {
  color: var(--primary-color);
  margin-bottom: 1.5rem;
  font-size: 2rem;
}

.interests-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
}

.interest-card {
  padding: 1.5rem;
  background: var(--bg-secondary);
  border-radius: 8px;
  border-left: 4px solid var(--primary-color);
}

.interest-card h3 {
  color: var(--primary-color);
  margin-bottom: 0.5rem;
}

.interest-card p {
  color: var(--text-light);
  line-height: 1.6;
}

.passions-list {
  list-style: none;
  padding: 0;
}

.passions-list li {
  padding: 1rem;
  margin-bottom: 0.5rem;
  background: var(--bg-secondary);
  border-radius: 5px;
  font-size: 1.1rem;
  transition: transform 0.2s;
}

.passions-list li:hover {
  transform: translateX(10px);
}

.goals-content p {
  margin-bottom: 1rem;
  line-height: 1.8;
  color: var(--text-light);
}

@media (max-width: 768px) {
  .about-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .profile-photo {
    max-width: 100%;
    width: 100%;
  }

  .interests-grid {
    grid-template-columns: 1fr;
  }

  .interests-section,
  .passions-section,
  .goals-section {
    padding: 1.5rem;
  }
}
</style>

