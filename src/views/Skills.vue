<template>
  <div class="skills">
    <div class="container">
      <h1 class="section-title">Skills & Resume</h1>

      <section class="skills-section">
        <h2>Technical Skills</h2>
        <div class="skills-container">
          <div 
            v-for="skill in skills" 
            :key="skill.name" 
            class="skill-item"
          >
            <div class="skill-header">
              <span class="skill-name">{{ skill.name }}</span>
              <span class="skill-percentage">{{ skill.level }}%</span>
            </div>
            <div class="skill-bar">
              <div 
                class="skill-progress" 
                :style="{ width: skill.level + '%' }"
              ></div>
            </div>
          </div>
        </div>
      </section>

      <section class="education-section">
        <h2>Educational Background</h2>
        <div class="education-timeline">
          <div 
            v-for="edu in education" 
            :key="edu.id" 
            class="education-card"
          >
            <div class="edu-year">{{ edu.year }}</div>
            <div class="edu-content">
              <h3>{{ edu.degree }}</h3>
              <p class="edu-institution">{{ edu.institution }}</p>
              <p class="edu-description">{{ edu.description }}</p>
            </div>
          </div>
        </div>
      </section>

      <section class="courses-section">
        <h2>Relevant Courses</h2>
        <div class="courses-grid">
          <div 
            v-for="course in courses" 
            :key="course" 
            class="course-tag"
          >
            {{ course }}
          </div>
        </div>
      </section>

      <section class="achievements-section">
        <h2>Awards & Achievements</h2>
        <div class="achievements-list">
          <div 
            v-for="achievement in achievements" 
            :key="achievement.id" 
            class="achievement-card"
          >
            <h3>{{ achievement.title }}</h3>
            <p class="achievement-year">{{ achievement.year }}</p>
            <p class="achievement-description">{{ achievement.description }}</p>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const skills = ref([
  { name: 'JavaScript', level: 85 },
  { name: 'Vue.js', level: 80 },
  { name: 'HTML/CSS', level: 90 },
  { name: 'Python', level: 75 },
  { name: 'Git', level: 80 },
  { name: 'Node.js', level: 70 },
  { name: 'React', level: 65 },
  { name: 'TypeScript', level: 70 }
])

const education = ref([
  {
    id: 1,
    year: '2020 - Present',
    degree: 'Bachelor of Science in Computer Science',
    institution: 'University Name',
    description: 'Focus on web development, software engineering, and data structures. Active member of the Computer Science Club.'
  },
  {
    id: 2,
    year: '2016 - 2020',
    degree: 'High School Diploma',
    institution: 'High School Name',
    description: 'Graduated with honors. Participated in programming competitions and robotics club.'
  }
])

const courses = ref([
  'Web Development',
  'Data Structures and Algorithms',
  'Software Engineering',
  'Database Systems',
  'Computer Networks',
  'Operating Systems',
  'Machine Learning',
  'User Interface Design'
])

const achievements = ref([
  {
    id: 1,
    title: 'Dean\'s List',
    year: '2022, 2023',
    description: 'Achieved outstanding academic performance with GPA above 3.8'
  },
  {
    id: 2,
    title: 'Hackathon Winner',
    year: '2023',
    description: 'First place in University Hackathon for best web application'
  },
  {
    id: 3,
    title: 'Open Source Contributor',
    year: '2023',
    description: 'Contributed to multiple open-source projects on GitHub'
  }
])
</script>

<style scoped>
.skills {
  padding: 2rem 0;
  min-height: calc(100vh - 200px);
}

.skills-section,
.education-section,
.courses-section,
.achievements-section {
  margin-bottom: 3rem;
  padding: 2rem;
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  box-shadow: var(--shadow);
  transition: all 0.3s ease;
}

.skills-section:hover,
.education-section:hover,
.courses-section:hover,
.achievements-section:hover {
  border-color: var(--border-light);
  box-shadow: var(--shadow-hover);
}

.skills-section h2,
.education-section h2,
.courses-section h2,
.achievements-section h2 {
  color: var(--primary-color);
  margin-bottom: 2rem;
  font-size: 2rem;
}

.skills-container {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.skill-item {
  margin-bottom: 1rem;
}

.skill-header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.5rem;
}

.skill-name {
  font-weight: 600;
  color: var(--text-color);
}

.skill-percentage {
  color: var(--primary-color);
  font-weight: 600;
}

.skill-bar {
  width: 100%;
  height: 25px;
  background: rgba(30, 41, 59, 0.5);
  border: 1px solid var(--border-color);
  border-radius: 15px;
  overflow: hidden;
  position: relative;
}

.skill-progress {
  height: 100%;
  background: var(--primary-color);
  border-radius: 15px;
  transition: width 1s ease-in-out;
  animation: slideIn 1s ease-out;
}

@keyframes slideIn {
  from {
    width: 0;
  }
}

.education-timeline {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.education-card {
  display: flex;
  gap: 2rem;
  padding: 1.5rem;
  background: var(--bg-secondary);
  border-radius: 8px;
  border-left: 4px solid var(--primary-color);
}

.edu-year {
  font-weight: bold;
  color: var(--primary-color);
  min-width: 150px;
  font-size: 1.1rem;
}

.edu-content h3 {
  color: var(--text-color);
  margin-bottom: 0.5rem;
  font-size: 1.3rem;
}

.edu-institution {
  color: var(--primary-color);
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.edu-description {
  color: var(--text-light);
  line-height: 1.6;
}

.courses-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.course-tag {
  padding: 0.75rem 1.5rem;
  background: rgba(6, 182, 212, 0.1);
  color: var(--primary-color);
  border: 1px solid var(--primary-color);
  border-radius: 25px;
  font-weight: 500;
  transition: all 0.2s ease;
}

.course-tag:hover {
  background: var(--primary-color);
  color: var(--bg-color);
  transform: scale(1.05);
  box-shadow: 0 0 15px rgba(6, 182, 212, 0.5);
}

.achievements-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
}

.achievement-card {
  padding: 1.5rem;
  background: var(--bg-secondary);
  border-radius: 8px;
  border-top: 4px solid var(--primary-color);
}

.achievement-card h3 {
  color: var(--primary-color);
  margin-bottom: 0.5rem;
  font-size: 1.3rem;
}

.achievement-year {
  color: var(--text-light);
  font-size: 0.9rem;
  margin-bottom: 0.5rem;
  opacity: 0.8;
}

.achievement-description {
  color: var(--text-light);
  line-height: 1.6;
}

@media (max-width: 768px) {
  .education-card {
    flex-direction: column;
    gap: 1rem;
  }

  .edu-year {
    min-width: auto;
  }

  .achievements-list {
    grid-template-columns: 1fr;
  }

  .skills-section,
  .education-section,
  .courses-section,
  .achievements-section {
    padding: 1.5rem;
  }
}
</style>

