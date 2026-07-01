<template>
  <section id="skills" class="skills" ref="sectionRef">
    <div class="skills-fade-in"></div>

    <div class="skills-bg">
      <div class="dot-field"></div>
      <div class="skills-orb"></div>
    </div>

    <div class="section-container">
      <p class="section-label reveal">— My Skills</p>
      <h2 class="section-title reveal" style="--delay: 0.1s">
        Technologies I Work With
      </h2>
      <p class="skills-intro reveal" style="--delay: 0.2s">
        A practical toolkit built through real projects — from Docker-based
        infrastructure to full-stack applications.
      </p>

      <div class="skills-grid">
        <div
          v-for="(group, gIndex) in skillGroups"
          :key="group.category"
          class="skill-category reveal"
          :style="{ '--delay': `${0.3 + gIndex * 0.12}s` }"
        >
          <h3 class="category-title">{{ group.category }}</h3>
          <div class="skill-badges">
            <div
              v-for="(skill, sIndex) in group.items"
              :key="skill.name"
              class="skill-badge reveal"
              :style="{ '--delay': `${0.4 + gIndex * 0.12 + sIndex * 0.06}s` }"
            >
              <span class="badge-icon" :style="{ color: skill.color }">{{
                skill.abbr
              }}</span>
              <span class="badge-label">{{ skill.name }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="skills-fade-out"></div>
  </section>
</template>

<
<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const skillGroups = [
  {
    category: "Frontend",
    items: [
      { name: "React.js", abbr: "⚛", color: "#61DAFB" },
      { name: "Vue 3", abbr: "V", color: "#4FC08D" },
      { name: "JavaScript", abbr: "JS", color: "#F7DF1E" },
      { name: "HTML5", abbr: "5", color: "#E34F26" },
      { name: "CSS3", abbr: "3", color: "#264DE4" },
      { name: "Bootstrap", abbr: "B", color: "#7952B3" },
      { name: "Tailwind CSS", abbr: "T", color: "#38BDF8" },
    ],
  },
  {
    category: "Backend",
    items: [
      { name: "Node.js", abbr: "N", color: "#68A063" },
      { name: "PHP", abbr: "P", color: "#777BB4" },
      { name: "Laravel", abbr: "L", color: "#FF2D20" },
      { name: "Python", abbr: "Py", color: "#3776AB" },
      { name: "Java", abbr: "J", color: "#E76F00" },
    ],
  },
  {
    category: "Databases",
    items: [
      { name: "MySQL", abbr: "My", color: "#4479A1" },
      { name: "PostgreSQL", abbr: "Pg", color: "#336791" },
      { name: "MongoDB", abbr: "M", color: "#47A248" },
    ],
  },
  {
    category: "Tools",
    items: [
      { name: "Vite", abbr: "⚡", color: "#FBBF24" },
      { name: "Git", abbr: "G", color: "#F05032" },
      { name: "VS Code", abbr: "VS", color: "#007ACC" },
    ],
  },
];

// Scroll-reveal via IntersectionObserver — elements get `.reveal` initially
// (hidden/offset) and `.is-visible` added once they scroll into view.
const sectionRef = ref(null);
let observer = null;

onMounted(() => {
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("is-visible");
          observer.unobserve(entry.target); // animate once, not every scroll
        }
      });
    },
    { threshold: 0.15 },
  );

  const revealEls = sectionRef.value.querySelectorAll(".reveal");
  revealEls.forEach((el) => observer.observe(el));
});

onUnmounted(() => {
  if (observer) observer.disconnect();
});
</script>

<style scoped>
.skills {
  position: relative;
  overflow: hidden;
  background-color: var(--color-primary);
  padding-top: var(--space-xl);
  padding-bottom: var(--space-xl);
}

/* Fade transitions - matching Hero/About pattern */
.skills-fade-in {
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

.skills-fade-out {
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

/* Scroll-reveal base state */
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

/* Category title underline draws in */
.category-title {
  position: relative;
  padding-bottom: 0.5rem;
  border-bottom: 1px solid rgba(251, 191, 36, 0.15);
  overflow: hidden;
}

.category-title::after {
  content: "";
  position: absolute;
  bottom: -1px;
  left: 0;
  width: 0;
  height: 1px;
  background-color: var(--color-accent);
  transition: width 0.8s ease 0.3s;
}

.skill-category.is-visible .category-title::after {
  width: 60px;
}

/* Enhanced badge hover */
.skill-badge {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  background-color: var(--color-secondary);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 8px;
  padding: 0.6rem 1rem;
  transition:
    transform 0.25s ease,
    border-color 0.25s ease,
    box-shadow 0.25s ease;
}

.skill-badge:hover {
  transform: translateY(-4px) scale(1.03);
  border-color: var(--color-accent);
  box-shadow: 0 8px 20px rgba(251, 191, 36, 0.15);
}

.skill-badge:hover .badge-icon {
  transform: scale(1.15);
}

.badge-icon {
  font-weight: 700;
  font-size: 0.9rem;
  width: 22px;
  text-align: center;
  transition: transform 0.25s ease;
  display: inline-block;
}

/* Motion background - dot field + single orb */
.skills-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
  pointer-events: none;
}

.dot-field {
  position: absolute;
  inset: 0;
  background-image: radial-gradient(
    rgba(251, 191, 36, 0.15) 10px,
    transparent 1.5px
  );
  background-size: 32px 32px;
  mask-image: radial-gradient(circle at 70% 40%, black 0%, transparent 65%);
  animation: dotPulse 8s ease-in-out infinite;
}

@keyframes dotPulse {
  0%,
  100% {
    opacity: 0.4;
  }
  50% {
    opacity: 0.9;
  }
}

.skills-orb {
  position: absolute;
  width: 380px;
  height: 380px;
  top: 10%;
  right: -5%;
  background: radial-gradient(circle, var(--color-accent), transparent 70%);
  opacity: 0.1;
  filter: blur(70px);
  border-radius: 50%;
  animation: drift1 16s ease-in-out infinite;
}

@keyframes drift1 {
  0%,
  100% {
    transform: translate(0, 0);
  }
  50% {
    transform: translate(-40px, 30px);
  }
}

/* Content */
.section-container {
  position: relative;
  z-index: 1;
}

.skills-intro {
  color: var(--color-text-body);
  max-width: 560px;
  margin-bottom: var(--space-xl);
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: var(--space-xl);
}

.category-title {
  font-size: 1.1rem;
  color: var(--color-accent);
  margin-bottom: var(--space-md);
  padding-bottom: 0.5rem;
  border-bottom: 1px solid rgba(251, 191, 36, 0.2);
}

.skill-badges {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.skill-badge {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  background-color: var(--color-secondary);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 8px;
  padding: 0.6rem 1rem;
  transition:
    transform 0.2s ease,
    border-color 0.2s ease;
}

.skill-badge:hover {
  transform: translateY(-3px);
  border-color: var(--color-accent);
}

.badge-icon {
  font-weight: 700;
  font-size: 0.9rem;
  width: 22px;
  text-align: center;
}

.badge-label {
  font-size: 0.9rem;
  color: var(--color-text-body);
  font-weight: 500;
}

/* Responsive */
@media (max-width: 800px) {
  .skills-grid {
    grid-template-columns: 1fr;
    gap: var(--space-lg);
  }
}
</style>
