<template>
  <section id="projects" class="projects" ref="sectionRef">
    <div class="projects-fade-in"></div>
    <div class="projects-bg">
      <div class="grid-pattern-alt"></div>
      <div class="proj-orb proj-orb-1"></div>
      <div class="proj-orb proj-orb-2"></div>
    </div>

    <div class="section-container">
      <p class="section-label reveal">— My Projects</p>
      <h2 class="section-title reveal" style="--delay: 0.1s">Featured Work</h2>
      <p class="projects-intro reveal" style="--delay: 0.2s">
        Real projects built end-to-end — from authentication systems to full
        dashboards, covering both frontend and backend.
      </p>

      <div class="projects-grid">
        <div
          v-for="(project, index) in projects"
          :key="project.name"
          class="project-card reveal"
          :style="{ '--delay': `${0.3 + index * 0.15}s` }"
        >
          <div class="card-glow"></div>
          <div class="card-header">
            <span class="project-tag">{{ project.tag }}</span>
            <h3 class="project-name">{{ project.name }}</h3>
          </div>

          <p class="project-desc">{{ project.description }}</p>

          <div class="tech-list">
            <span v-for="tech in project.tech" :key="tech" class="tech-pill">
              {{ tech }}
            </span>
          </div>

          <div class="card-links">
            <a
              :href="project.github"
              target="_blank"
              rel="noopener"
              class="link-btn"
            >
              Code
              <svg viewBox="0 0 24 24" width="14" height="14">
                <path
                  fill="currentColor"
                  d="M12 2C6.48 2 2 6.48 2 12c0 4.42 2.87 8.17 6.84 9.5.5.09.66-.22.66-.48v-1.7c-2.78.6-3.37-1.34-3.37-1.34-.46-1.16-1.11-1.47-1.11-1.47-.91-.62.07-.6.07-.6 1 .07 1.53 1.03 1.53 1.03.89 1.52 2.34 1.08 2.91.83.09-.65.35-1.09.63-1.34-2.22-.25-4.56-1.11-4.56-4.94 0-1.09.39-1.98 1.03-2.68-.1-.25-.45-1.27.1-2.65 0 0 .84-.27 2.75 1.03a9.4 9.4 0 0 1 5 0c1.91-1.3 2.75-1.03 2.75-1.03.55 1.38.2 2.4.1 2.65.64.7 1.03 1.59 1.03 2.68 0 3.84-2.35 4.68-4.58 4.93.36.31.68.92.68 1.85v2.75c0 .26.16.57.67.48A10.01 10.01 0 0 0 22 12c0-5.52-4.48-10-10-10z"
                />
              </svg>
            </a>
            <a
              :href="project.live"
              target="_blank"
              rel="noopener"
              class="link-btn link-btn-primary"
            >
              Live Demo
              <span class="arrow">→</span>
            </a>
          </div>
        </div>
      </div>
    </div>

    <div class="projects-fade-out"></div>
  </section>
</template>

<
<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const projects = [
  {
    name: "Sentinel Lite",
    tag: "Frontend Dashboard",
    description:
      "A production-quality security monitoring dashboard built from scratch: authentication, protected routing, a collapsible sidebar, auto-refreshing stats, filterable alerts with debounced search, a full CRUD devices module, dark mode settings, and a global toast notification system.",
    tech: ["Vue 3", "Pinia", "Vue Router", "Axios", "Tailwind CSS"],
    github: "https://github.com/melichris/sentinel-lite",
    live: "#",
  },
  {
    name: "Driver Hiring Management System",
    tag: "Frontend Application",
    description:
      "The frontend for a driver hiring management platform, built to streamline how driver applications and hiring workflows are handled.",
    tech: ["CSS", "JavaScript"],
    github: "https://github.com/melichris/Driver_Hiring_Management_System",
    live: "#",
  },
  {
    name: "Face Mask Detection",
    tag: "AI / Computer Vision",
    description:
      "A biometric facial recognition system that detects whether a user is wearing a face mask, using computer vision and deep learning for real-time verification.",
    tech: ["Python", "OpenCV", "TensorFlow", "Keras"],
    github: "https://github.com/melichris/Face_Mask_Detection",
    live: null,
  },
  {
    name: "Exam Surveillance System with AI",
    tag: "AI / Malpractice Detection",
    description:
      "An AI-driven exam surveillance system designed to detect malpractice during examinations, using computer vision and deep learning to support automated academic integrity monitoring.",
    tech: ["Python", "OpenCV", "TensorFlow", "Keras", "PyTorch", "Mediapipe"],
    github: "https://github.com/melichris/exam_surveillance_system_with_AI",
    live: null,
  },
  {
    name: "MCQ Managements System",
    tag: "Multiple Choice Question Management",
    description:
      "A comprehensive system for managing multiple choice questions, including creation, editing, and automated grading capabilities.",
    tech: ["java", "Spring Boot", "MySQL", "Thymeleaf"],
    github: "https://github.com/melichris/MCQ_Management_System",
    live: null,
  },
];

const sectionRef = ref(null);
let observer = null;

onMounted(() => {
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("is-visible");
          observer.unobserve(entry.target);
        }
      });
    },
    { threshold: 0.15 },
  );
  sectionRef.value
    .querySelectorAll(".reveal")
    .forEach((el) => observer.observe(el));
});

onUnmounted(() => {
  if (observer) observer.disconnect();
});
</script>

<style scoped>
.projects {
  position: relative;
  overflow: hidden;
  background-color: var(--color-primary);
  padding-top: var(--space-xl);
  padding-bottom: var(--space-xl);
}

/* Fade transitions */
.projects-fade-in {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 160px;
  background: linear-gradient(
    to bottom,
    var(--color-primary) 0%,
    transparent 100%
  );
  z-index: 2;
  pointer-events: none;
}

.projects-fade-out {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 160px;
  background: linear-gradient(
    to bottom,
    transparent 0%,
    var(--color-primary) 100%
  );
  z-index: 2;
  pointer-events: none;
}

/* Motion background */
.projects-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
  pointer-events: none;
}

.grid-pattern-alt {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(251, 191, 36, 0.05) 15px, transparent 1px),
    linear-gradient(90deg, rgba(251, 191, 36, 0.05) 15px, transparent 1px);
  background-size: 60px 60px;
  mask-image: radial-gradient(circle at 30% 60%, black 0%, transparent 70%);
  animation: gridPulse 5s ease-in-out infinite;
}

@keyframes gridPulse {
  0%,
  100% {
    opacity: 0.4;
  }
  50% {
    opacity: 0.9;
  }
}

.proj-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(70px);
  opacity: 0.12;
}

.proj-orb-1 {
  width: 340px;
  height: 340px;
  top: 15%;
  left: -5%;
  background: radial-gradient(circle, var(--color-accent), transparent 70%);
  animation: drift1 18s ease-in-out infinite;
}

.proj-orb-2 {
  width: 280px;
  height: 280px;
  bottom: 10%;
  right: -5%;
  background: radial-gradient(circle, var(--color-accent), transparent 70%);
  animation: drift2 22s ease-in-out infinite;
}

@keyframes drift1 {
  0%,
  100% {
    transform: translate(0, 0);
  }
  50% {
    transform: translate(30px, 40px);
  }
}

@keyframes drift2 {
  0%,
  100% {
    transform: translate(0, 0);
  }
  50% {
    transform: translate(-30px, -30px);
  }
}

/* Content */
.section-container {
  position: relative;
  z-index: 1;
}

.projects-intro {
  color: var(--color-text-body);
  max-width: 560px;
  margin-bottom: var(--space-xl);
}

/* Reveal (reuse pattern) */
.reveal {
  opacity: 0;
  transform: translateY(24px);
  transition:
    opacity 0.6s ease,
    transform 0.6s ease;
  transition-delay: var(--delay, 0s);
}

.reveal.is-visible {
  opacity: 1;
  transform: translateY(0);
}

/* Project card */
.project-card {
  position: relative;
  background-color: var(--color-secondary);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 14px;
  padding: var(--space-lg);
  display: flex;
  flex-direction: column;
  gap: var(--space-sm);
  transition:
    transform 0.3s ease,
    border-color 0.3s ease,
    box-shadow 0.3s ease;
  overflow: hidden;
}

.project-card:hover {
  transform: translateY(-8px);
  border-color: rgba(251, 191, 36, 0.4);
  box-shadow: 0 16px 32px rgba(0, 0, 0, 0.35);
}

/* Infinite ambient glow inside each card */
.card-glow {
  position: absolute;
  top: -40%;
  right: -30%;
  width: 180px;
  height: 180px;
  background: radial-gradient(
    circle,
    rgba(251, 191, 36, 0.15),
    transparent 20%
  );
  border-radius: 50%;
  animation: cardPulse 5s ease-in-out infinite;
  pointer-events: none;
}

@keyframes cardPulse {
  0%,
  100% {
    opacity: 0.5;
    transform: scale(1);
  }
  50% {
    opacity: 1;
    transform: scale(1.15);
  }
}

.project-tag {
  display: inline-block;
  font-size: 0.7rem;
  font-weight: 600;
  letter-spacing: 0.5px;
  color: var(--color-accent);
  background-color: rgba(251, 191, 36, 0.1);
  border: 1px solid rgba(251, 191, 36, 0.25);
  padding: 0.25rem 0.6rem;
  border-radius: 20px;
  margin-bottom: 0.5rem;
}

.project-name {
  font-size: 1.25rem;
}

.project-desc {
  color: var(--color-text-body);
  font-size: 0.9rem;
  line-height: 1.6;
  flex-grow: 1;
}

.tech-list {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
}

.tech-pill {
  font-size: 0.75rem;
  color: var(--color-text-muted);
  background-color: rgba(255, 255, 255, 0.05);
  padding: 0.25rem 0.6rem;
  border-radius: 6px;
}

.card-links {
  display: flex;
  gap: var(--space-sm);
  margin-top: var(--space-sm);
}

.link-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  font-size: 0.85rem;
  font-weight: 500;
  color: var(--color-text-body);
  border: 1px solid rgba(255, 255, 255, 0.15);
  padding: 0.5rem 0.9rem;
  border-radius: 6px;
  transition:
    border-color 0.2s ease,
    color 0.2s ease;
}

.link-btn:hover {
  border-color: var(--color-accent);
  color: var(--color-accent);
}

.link-btn-primary {
  background-color: var(--color-accent);
  color: var(--color-primary);
  border-color: var(--color-accent);
  font-weight: 600;
}

.link-btn-primary:hover {
  opacity: 0.9;
  color: var(--color-primary);
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: var(--space-lg);
}

/* Responsive */
@media (max-width: 1000px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
}
</style>
