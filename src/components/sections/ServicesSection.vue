<template>
  <section id="services" class="services" ref="sectionRef">
    <div class="services-fade-in"></div>

    <div class="services-bg">
      <div class="dot-field-alt"></div>
      <div class="serv-orb"></div>
    </div>

    <div class="section-container">
      <p class="section-label reveal">— Services</p>
      <h2 class="section-title reveal" style="--delay: 0.1s">
        What I Can Do For You
      </h2>
      <p class="services-intro reveal" style="--delay: 0.2s">
        From frontend interfaces to full backend systems — I build complete,
        production-ready solutions.
      </p>

      <div class="services-grid">
        <div
          v-for="(service, index) in services"
          :key="service.title"
          class="service-card reveal"
          :style="{ '--delay': `${0.3 + index * 0.12}s` }"
        >
          <div class="glass-shine"></div>
          <div class="service-icon">{{ service.icon }}</div>
          <h3 class="service-title">{{ service.title }}</h3>
          <p class="service-desc">{{ service.description }}</p>
        </div>
      </div>
    </div>

    <div class="services-fade-out"></div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const services = [
  {
    icon: "</>",
    title: "Frontend Development",
    description:
      "Responsive, interactive interfaces built with Vue 3 and React — from landing pages to full application dashboards.",
  },
  {
    icon: "⚙",
    title: "Backend & API Development",
    description:
      "RESTful APIs and server-side logic using Node.js, PHP/Laravel, or Python — with authentication, database design, and secure architecture.",
  },
  {
    icon: "⬢",
    title: "Full-Stack Web Applications",
    description:
      "End-to-end applications combining frontend, backend, and database — built, tested, and deployed as a complete product.",
  },
  {
    icon: "☁",
    title: "Deployment & Infrastructure",
    description:
      "Docker-based deployment and infrastructure setup, drawing on hands-on experience deploying and managing production systems.",
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
.services {
  position: relative;
  overflow: hidden;
  background-color: var(--color-primary);
  padding-top: var(--space-xl);
  padding-bottom: var(--space-xl);
}

.services-fade-in {
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

.services-fade-out {
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

.services-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
  pointer-events: none;
}

.dot-field-alt {
  position: absolute;
  inset: 0;
  background-image: radial-gradient(
    rgba(251, 191, 36, 0.12) 10px,
    transparent 10px
  );
  background-size: 40px 40px;
  mask-image: radial-gradient(circle at 80% 70%, black 0%, transparent 65%);
  animation: dotPulse 9s ease-in-out infinite;
}

@keyframes dotPulse {
  0%,
  100% {
    opacity: 0.4;
  }
  50% {
    opacity: 0.85;
  }
}

.serv-orb {
  position: absolute;
  width: 360px;
  height: 360px;
  top: 20%;
  left: -8%;
  background: radial-gradient(circle, var(--color-accent), transparent 70%);
  opacity: 0.1;
  filter: blur(70px);
  border-radius: 50%;
  animation: drift3 20s ease-in-out infinite;
}

@keyframes drift3 {
  0%,
  100% {
    transform: translate(0, 0);
  }
  50% {
    transform: translate(35px, -25px);
  }
}

.section-container {
  position: relative;
  z-index: 1;
}

.services-intro {
  color: var(--color-text-body);
  max-width: 560px;
  margin-bottom: var(--space-xl);
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: var(--space-lg);
}

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

.service-card:hover {
  transform: translateY(-6px);
  border-color: rgba(251, 191, 36, 0.4);
}

..service-card {
  position: relative;
  background: rgba(255, 255, 255, 0.04);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 18px;
  padding: var(--space-lg) var(--space-md);
  text-align: left;
  overflow: hidden;
  transition:
    transform 0.35s ease,
    border-color 0.35s ease,
    background 0.35s ease,
    box-shadow 0.35s ease;
  box-shadow:
    0 8px 32px rgba(0, 0, 0, 0.25),
    inset 0 1px 0 rgba(255, 255, 255, 0.1);
}

.service-card:hover {
  transform: translateY(-8px);
  background: rgba(255, 255, 255, 0.07);
  border-color: rgba(251, 191, 36, 0.45);
  box-shadow:
    0 16px 40px rgba(0, 0, 0, 0.35),
    0 0 24px rgba(251, 191, 36, 0.12),
    inset 0 1px 0 rgba(255, 255, 255, 0.15);
}

/* Subtle diagonal shine sweep across the glass on hover */
.glass-shine {
  position: absolute;
  top: 0;
  left: -100%;
  width: 60%;
  height: 100%;
  background: linear-gradient(
    115deg,
    transparent 0%,
    rgba(255, 255, 255, 0.08) 50%,
    transparent 100%
  );
  transform: skewX(-20deg);
  transition: left 0.7s ease;
  pointer-events: none;
}

.service-card:hover .glass-shine {
  left: 130%;
}

.service-icon {
  width: 52px;
  height: 52px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(251, 191, 36, 0.08);
  backdrop-filter: blur(6px);
  border: 1px solid rgba(251, 191, 36, 0.3);
  border-radius: 12px;
  color: var(--color-accent);
  font-size: 1.3rem;
  font-weight: 700;
  margin-bottom: var(--space-md);
  animation: iconFloat 3.5s ease-in-out infinite;
}

@keyframes iconFloat {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-6px);
  }
}

.service-title {
  font-size: 1.1rem;
  margin-bottom: 0.5rem;
}

.service-desc {
  color: var(--color-text-body);
  font-size: 0.88rem;
  line-height: 1.6;
}

@media (max-width: 1000px) {
  .services-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .services-grid {
    grid-template-columns: 1fr;
  }
}
</style>
