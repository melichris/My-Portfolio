<template>
  <section id="projects" class="projects" ref="sectionRef">
    <div class="projects-fade-in"></div>
    <div class="projects-bg">
      <div class="grid-pattern-alt"></div>
      <div class="proj-orb"></div>
    </div>

    <div class="section-container">
      <div class="projects-header">
        <div>
          <p class="section-label reveal">— My Projects</p>
          <h2 class="section-title reveal" style="--delay:0.1s">Featured Projects</h2>
        </div>
        <a href="https://github.com/melichris" target="_blank" class="view-all reveal" style="--delay:0.1s">View All
          Projects <span>→</span></a>
      </div>

      <div class="projects-list">
        <div v-for="(p, i) in projects" :key="p.name" class="project-card reveal"
          :style="{ '--delay': `${0.2 + i * 0.12}s` }">
          <div class="thumb"><img :src="thumb" :alt="p.name" /></div>
          <div class="p-body">
            <div class="p-top">
              <h3>{{ p.name }}</h3>
              <span class="tag">{{ p.tag }}</span>
            </div>
            <p class="p-desc">{{ p.description }}</p>
            <div class="tech-icons">
              <span v-for="t in p.tech" :key="t.name" class="tech-icon" :title="t.name" :style="{ color: t.color }">
                <svg v-if="t.svg" viewBox="0 0 24 24" width="18" height="18" v-html="t.svg"></svg>
                <span v-else class="tech-abbr">{{ t.abbr }}</span>
              </span>
            </div>
            <a :href="p.github" target="_blank" class="view-project">View Project <span>→</span></a>
          </div>
        </div>
      </div>
    </div>
    <div class="projects-fade-out"></div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import thumb from '../../assets/project-placeholder.png'

const VUE = { name: 'Vue 3', color: '#4FC08D', svg: `<path fill="currentColor" d="M2 3h4l6 10 6-10h4L12 21z"/><path fill="currentColor" opacity="0.6" d="M6 3h3.2L12 7.8 14.8 3H18l-6 10z"/>` }
const JS = { name: 'JavaScript', color: '#F7DF1E', svg: `<rect x="2" y="2" width="20" height="20" rx="3" fill="none" stroke="currentColor" stroke-width="1.4"/><text x="12" y="16.5" font-size="9" font-weight="700" text-anchor="middle" fill="currentColor">JS</text>` }
const PY = { name: 'Python', color: '#3776AB', svg: `<path fill="currentColor" d="M12 2c-3 0-5 1-5 4v2h5v1H4c-2 0-3 2-3 5s1 5 3 5h2v-3c0-2 2-4 4-4h4c2 0 3-1 3-3V6c0-2-2-4-5-4zm-2 3a1 1 0 110 2 1 1 0 010-2z"/><path fill="currentColor" opacity="0.55" d="M12 22c3 0 5-1 5-4v-2h-5v-1h8c2 0 3-2 3-5s-1-5-3-5h-2v3c0 2-2 4-4 4H10c-2 0-3 1-3 3v3c0 2 2 4 5 4zm2-3a1 1 0 110-2 1 1 0 010 2z"/>` }
const CSS3 = { name: 'CSS3', color: '#264DE4', svg: `<path fill="none" stroke="currentColor" stroke-width="1.3" d="M4 4h16l-1.4 15L12 21l-6.6-2z"/><path fill="none" stroke="currentColor" stroke-width="1.3" d="M17 8H7l.3 3h9l-.4 4-3.9 1.2-3.8-1.2-.2-2.2"/>` }
const abbr = (name, color, abbr) => ({ name, color, abbr })

const projects = [
  {
    name: 'Sentinel Lite', tag: 'Frontend Dashboard', github: 'https://github.com/melichris/sentinel-lite',
    description: 'A production-quality security dashboard: auth, protected routing, CRUD devices, dark mode, and global toast notifications.',
    tech: [VUE, abbr('Pinia', '#FFD859', 'P'), abbr('Vue Router', '#4FC08D', 'VR'), abbr('Axios', '#5A29E4', 'Ax'), abbr('Tailwind CSS', '#38BDF8', 'TW')]
  },
  {
    name: 'Driver Hiring Management System', tag: 'Frontend App', github: 'https://github.com/melichris/Driver_Hiring_Management_System',
    description: 'Frontend for a driver hiring platform, streamlining application and hiring workflows.',
    tech: [CSS3, JS]
  },
  {
    name: 'Face Mask Detection', tag: 'AI / Computer Vision', github: 'https://github.com/melichris/Face_Mask_Detection',
    description: 'Facial recognition system detecting mask compliance in real time using computer vision.',
    tech: [PY, abbr('OpenCV', '#5C3EE8', 'CV'), abbr('TensorFlow', '#FF6F00', 'TF'), abbr('Keras', '#D00000', 'K')]
  },
  {
    name: 'Exam Surveillance System with AI', tag: 'AI / Malpractice Detection', github: 'https://github.com/melichris/exam_surveillance_system_with_AI',
    description: 'AI-driven surveillance system detecting exam malpractice via automated monitoring.',
    tech: [PY, abbr('OpenCV', '#5C3EE8', 'CV'), abbr('TensorFlow', '#FF6F00', 'TF'), abbr('PyTorch', '#EE4C2C', 'PT'), abbr('Mediapipe', '#00A3E0', 'MP')]
  },
]

const sectionRef = ref(null)
let observer = null
onMounted(() => {
  observer = new IntersectionObserver((entries) => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('is-visible'); observer.unobserve(e.target) } })
  }, { threshold: 0.15 })
  sectionRef.value.querySelectorAll('.reveal').forEach(el => observer.observe(el))
})
onUnmounted(() => observer?.disconnect())
</script>

<style scoped>
.projects {
  position: relative;
  overflow: hidden;
  background-color: var(--color-primary);
  padding-top: var(--space-xl);
  padding-bottom: var(--space-xl);
}

.projects-fade-in {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 160px;
  background: linear-gradient(to bottom, var(--color-primary) 0%, transparent 100%);
  z-index: 2;
  pointer-events: none;
}

.projects-fade-out {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 160px;
  background: linear-gradient(to bottom, transparent 0%, var(--color-primary) 100%);
  z-index: 2;
  pointer-events: none;
}

.projects-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
  pointer-events: none;
}

.grid-pattern-alt {
  position: absolute;
  inset: 0;
  background-image: linear-gradient(rgba(251, 191, 36, 0.05) 1px, transparent 1px), linear-gradient(90deg, rgba(251, 191, 36, 0.05) 1px, transparent 1px);
  background-size: 60px 60px;
  mask-image: radial-gradient(circle at 30% 60%, black 0%, transparent 70%);
  animation: gridPulse 7s ease-in-out infinite;
}

@keyframes gridPulse {

  0%,
  100% {
    opacity: 0.4
  }

  50% {
    opacity: 0.9
  }
}

.proj-orb {
  position: absolute;
  width: 340px;
  height: 340px;
  top: 15%;
  left: -5%;
  border-radius: 50%;
  filter: blur(70px);
  opacity: 0.12;
  background: radial-gradient(circle, var(--color-accent), transparent 70%);
  animation: drift 18s ease-in-out infinite;
}

@keyframes drift {

  0%,
  100% {
    transform: translate(0, 0)
  }

  50% {
    transform: translate(30px, 40px)
  }
}

.section-container {
  position: relative;
  z-index: 1;
}

.projects-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: var(--space-xl);
}

.view-all {
  color: var(--color-accent);
  font-size: 0.9rem;
  font-weight: 600;
  transition: transform 0.2s ease;
}

.view-all:hover {
  transform: translateX(4px);
}

.reveal {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.6s ease, transform 0.6s ease;
  transition-delay: var(--delay, 0s);
}

.reveal.is-visible {
  opacity: 1;
  transform: translateY(0);
}

.projects-list {
  display: flex;
  flex-direction: column;
  gap: var(--space-lg);
}

.project-card {
  display: grid;
  grid-template-columns: 1.5fr 1fr 1fr;
  gap: var(--space-lg);
  background-color: var(--color-secondary);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 14px;
  overflow: hidden;
  transition: transform 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
}

.project-card:hover {
  transform: translateY(-6px);
  border-color: rgba(251, 191, 36, 0.35);
  box-shadow: 0 16px 32px rgba(0, 0, 0, 0.35);
}

.thumb {
  overflow: hidden;
}

.thumb img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.5s ease;
}

.project-card:hover .thumb img {
  transform: scale(1.06);
}

.p-body {
  padding: var(--space-lg) var(--space-lg) var(--space-lg) 0;
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}

.p-top {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  flex-wrap: wrap;
}

.p-top h3 {
  font-size: 1.2rem;
}

.tag {
  font-size: 0.7rem;
  font-weight: 600;
  color: var(--color-accent);
  border: 1px solid rgba(251, 191, 36, 0.35);
  padding: 0.2rem 0.6rem;
  border-radius: 20px;
}

.p-desc {
  color: var(--color-text-body);
  font-size: 0.9rem;
  line-height: 1.6;
}

.tech-icons {
  display: flex;
  gap: 0.6rem;
  flex-wrap: wrap;
  margin-top: 0.25rem;
}

.tech-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 34px;
  height: 34px;
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.05);
  transition: transform 0.2s ease;
}

.tech-icon:hover {
  transform: translateY(-3px);
}

.tech-abbr {
  font-size: 0.65rem;
  font-weight: 700;
}

.view-project {
  color: var(--color-accent);
  font-size: 0.9rem;
  font-weight: 600;
  margin-top: 0.5rem;
  transition: transform 0.2s ease;
}

.view-project:hover {
  transform: translateX(4px);
}

@media (max-width: 800px) {
  .project-card {
    grid-template-columns: 1fr;
  }

  .thumb {
    height: 200px;
  }

  .p-body {
    padding: var(--space-md);
  }

  .projects-header {
    flex-direction: column;
    align-items: flex-start;
    gap: 0.5rem;
  }
}
</style>
