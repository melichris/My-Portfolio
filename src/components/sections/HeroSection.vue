<template>
  <section id="home" class="hero">
    <!-- Motion background layer -->
    <div class="hero-bg">
      <div class="grid-pattern"></div>
      <div
        class="orb orb-1"
        :style="{
          transform: `translate(${parallaxX * -12}px, ${parallaxY * -12}px)`,
        }"
      ></div>
      <div
        class="orb orb-2"
        :style="{
          transform: `translate(${parallaxX * 10}px, ${parallaxY * 10}px)`,
        }"
      ></div>
      <div
        class="orb orb-3"
        :style="{
          transform: `translate(${parallaxX * -8}px, ${parallaxY * 8}px)`,
        }"
      ></div>
    </div>

    <div class="hero-container" :class="{ 'is-loaded': heroLoaded }">
      <div class="hero-content">
        <p class="hero-greeting hero-anim" style="--anim-delay: 0s">
          Hello, I'm
        </p>
        <h1 class="hero-name hero-anim" style="--anim-delay: 0.1s">
          Meli <span class="accent-text">Christian</span>
        </h1>

        <!-- Status badge -->
        <div class="status-badge hero-anim" style="--anim-delay: 0.2s">
          <span class="status-dot"></span>
          Available for work
        </div>

        <h2 class="hero-role hero-anim" style="--anim-delay: 0.25s">
          <span class="typed-text">{{ displayedText }}</span
          ><span class="cursor blink">|</span>
        </h2>
        <p class="hero-desc hero-anim" style="--anim-delay: 0.35s">
          I build scalable and high-performance web applications that deliver
          great user experiences.
        </p>

        <div class="hero-actions hero-anim" style="--anim-delay: 0.45s">
          <a href="/Meli_Christian_SWE_CV.pdf" class="btn-primary" download>
            Download CV
            <span class="icon-download">↓</span>
          </a>
          <a href="#contact" class="btn-text">
            Contact Me <span class="arrow">→</span>
          </a>
        </div>

        <div class="hero-social">
          <span class="follow-label">Follow Me</span>
          <a
            href="https://github.com/melichris"
            target="_blank"
            rel="noopener"
            aria-label="GitHub"
          >
            <svg viewBox="0 0 24 24" width="30" height="30">
              <path
                fill="currentColor"
                d="M12 2C6.48 2 2 6.48 2 12c0 4.42 2.87 8.17 6.84 9.5.5.09.66-.22.66-.48v-1.7c-2.78.6-3.37-1.34-3.37-1.34-.46-1.16-1.11-1.47-1.11-1.47-.91-.62.07-.6.07-.6 1 .07 1.53 1.03 1.53 1.03.89 1.52 2.34 1.08 2.91.83.09-.65.35-1.09.63-1.34-2.22-.25-4.56-1.11-4.56-4.94 0-1.09.39-1.98 1.03-2.68-.1-.25-.45-1.27.1-2.65 0 0 .84-.27 2.75 1.03a9.4 9.4 0 0 1 5 0c1.91-1.3 2.75-1.03 2.75-1.03.55 1.38.2 2.4.1 2.65.64.7 1.03 1.59 1.03 2.68 0 3.84-2.35 4.68-4.58 4.93.36.31.68.92.68 1.85v2.75c0 .26.16.57.67.48A10.01 10.01 0 0 0 22 12c0-5.52-4.48-10-10-10z"
              />
            </svg>
          </a>
          <a
            href="https://www.linkedin.com/in/meli-christian/"
            target="_blank"
            rel="noopener"
            aria-label="LinkedIn"
          >
            <svg viewBox="0 0 24 24" width="30" height="30">
              <path
                fill="currentColor"
                d="M20.45 20.45h-3.56v-5.57c0-1.33-.02-3.04-1.85-3.04-1.85 0-2.14 1.45-2.14 2.94v5.67H9.34V9h3.42v1.56h.05c.48-.9 1.64-1.85 3.38-1.85 3.6 0 4.27 2.37 4.27 5.46v6.28zM5.34 7.43a2.06 2.06 0 1 1 0-4.12 2.06 2.06 0 0 1 0 4.12zM7.12 20.45H3.56V9h3.56v11.45z"
              />
            </svg>
          </a>
          <a href="mailto:melichris.work@gmail.com" aria-label="Email">
            <svg viewBox="0 0 24 24" width="30" height="30">
              <path
                fill="currentColor"
                d="M20 4H4a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V6a2 2 0 0 0-2-2zm0 4-8 5-8-5V6l8 5 8-5v2z"
              />
            </svg>
          </a>
        </div>
      </div>

      <!-- Photo with floating icons -->
      <div
        class="hero-photo-wrap hero-anim"
        :style="{
          '--anim-delay': '0.3s',
          transform: `translate(${parallaxX * 8}px, ${parallaxY * 8}px)`,
        }"
      >
        <div class="glow"></div>
        <img
          src="../../assets/profile-bg.png"
          alt="Meli Christian"
          class="hero-photo"
        />

        <div
          v-for="(icon, index) in orbitIcons"
          :key="icon.id"
          class="float-icon"
          :style="{
            left: icon.style.left,
            top: icon.style.top,
            color: icon.color,
            '--icon-color': icon.color,
            '--i': index,
          }"
        >
          <svg
            viewBox="0 0 24 24"
            width="70"
            height="70"
            v-html="icon.svg"
          ></svg>
        </div>
      </div>
    </div>

    <!-- Scroll-down indicator -->
    <a
      href="#about"
      class="scroll-indicator"
      aria-label="Scroll to About section"
    >
      <span class="scroll-text">Scroll</span>
      <span class="scroll-chevron">⌄</span>
    </a>

    <div class="hero-fade"></div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted, computed } from "vue";

// Titles to cycle through — edit this list to match how you want to
// present yourself (keep them short so they fit on one line on mobile)
const titles = [
  "Full Stack Developer",
  "Vue.js Developer",
  "Backend Engineer",
  "API Architect",
];

const displayedText = ref("");
const showCursor = ref(true);

let titleIndex = 0;
let charIndex = 0;
let isDeleting = false;
let timeoutId = null;

const TYPE_SPEED = 90; // ms per character while typing
const DELETE_SPEED = 45; // ms per character while deleting
const HOLD_TIME = 1800; // ms to pause once a title is fully typed
const GAP_TIME = 400; // ms pause once fully deleted before next title

// Entrance animation trigger
const heroLoaded = ref(false);

// Mouse parallax (desktop only)
const parallaxX = ref(0);
const parallaxY = ref(0);
const isDesktop = ref(window.innerWidth > 900);

const techIcons = [
  {
    id: "vue",
    color: "#4FC08D",
    svg: `<path fill="currentColor" d="M2 3h4l6 10 6-10h4L12 21z"/><path fill="currentColor" opacity="0.6" d="M6 3h3.2L12 7.8 14.8 3H18l-6 10z"/>`,
  },
  {
    id: "react",
    color: "#61DAFB",
    svg: `<ellipse cx="12" cy="12" rx="10" ry="4.2" fill="none" stroke="currentColor" stroke-width="1.4"/><ellipse cx="12" cy="12" rx="10" ry="4.2" fill="none" stroke="currentColor" stroke-width="1.4" transform="rotate(60 12 12)"/><ellipse cx="12" cy="12" rx="10" ry="4.2" fill="none" stroke="currentColor" stroke-width="1.4" transform="rotate(120 12 12)"/><circle cx="12" cy="12" r="1.8" fill="currentColor"/>`,
  },
  {
    id: "js",
    color: "#F7DF1E",
    svg: `<rect x="2" y="2" width="20" height="20" rx="3" fill="none" stroke="currentColor" stroke-width="1.4"/><text x="12" y="16.5" font-size="9" font-weight="700" text-anchor="middle" fill="currentColor">JS</text>`,
  },
  {
    id: "php",
    color: "#777BB4",
    svg: `<ellipse cx="12" cy="12" rx="10" ry="6" fill="none" stroke="currentColor" stroke-width="1.4"/><text x="12" y="15" font-size="6.5" font-weight="700" text-anchor="middle" fill="currentColor" font-style="italic">php</text>`,
  },
  {
    id: "python",
    color: "#3776AB",
    svg: `<path fill="currentColor" d="M12 2c-3 0-5 1-5 4v2h5v1H4c-2 0-3 2-3 5s1 5 3 5h2v-3c0-2 2-4 4-4h4c2 0 3-1 3-3V6c0-2-2-4-5-4zm-2 3a1 1 0 110 2 1 1 0 010-2z"/><path fill="currentColor" opacity="0.55" d="M12 22c3 0 5-1 5-4v-2h-5v-1h8c2 0 3-2 3-5s-1-5-3-5h-2v3c0 2-2 4-4 4H10c-2 0-3 1-3 3v3c0 2 2 4 5 4zm2-3a1 1 0 110-2 1 1 0 010 2z"/>`,
  },
  {
    id: "mysql",
    color: "#4479A1",
    svg: `<ellipse cx="12" cy="6" rx="8" ry="3" fill="none" stroke="currentColor" stroke-width="1.4"/><path fill="none" stroke="currentColor" stroke-width="1.4" d="M4 6v12c0 1.7 3.6 3 8 3s8-1.3 8-3V6"/><path fill="none" stroke="currentColor" stroke-width="1.2" d="M4 12c0 1.7 3.6 3 8 3s8-1.3 8-3"/>`,
  },
  {
    id: "git",
    color: "#F05032",
    svg: `<circle cx="6" cy="6" r="2.2" fill="currentColor"/><circle cx="18" cy="18" r="2.2" fill="currentColor"/><circle cx="18" cy="9" r="2.2" fill="currentColor"/><path fill="none" stroke="currentColor" stroke-width="1.4" d="M6 8v6a4 4 0 004 4h6M18 11v5"/>`,
  },
];

// Arrange all icons evenly around a circular orbit outside the photo
const orbitIcons = computed(() => {
  const total = techIcons.length;
  const radius = 58; // % from center — pushes icons just past the photo edge
  return techIcons.map((icon, i) => {
    const angle = (360 / total) * i - 90; // start at 12 o'clock, go clockwise
    const rad = (angle * Math.PI) / 180;
    const x = 50 + radius * Math.cos(rad);
    const y = 50 + radius * Math.sin(rad);
    return { ...icon, style: { left: `${x}%`, top: `${y}%` } };
  });
});

function handleMouseMove(e) {
  if (!isDesktop.value) return;
  const { innerWidth, innerHeight } = window;
  // Normalize to -1..1 range, then scale down to a subtle shift
  parallaxX.value = (e.clientX / innerWidth - 0.5) * 2;
  parallaxY.value = (e.clientY / innerHeight - 0.5) * 2;
}

function handleResize() {
  isDesktop.value = window.innerWidth > 900;
}

onMounted(() => {
  // Trigger entrance animation shortly after mount
  requestAnimationFrame(() => {
    setTimeout(() => {
      heroLoaded.value = true;
    }, 100);
  });

  window.addEventListener("mousemove", handleMouseMove);
  window.addEventListener("resize", handleResize);
});

onUnmounted(() => {
  window.removeEventListener("mousemove", handleMouseMove);
  window.removeEventListener("resize", handleResize);
});

function tick() {
  const currentTitle = titles[titleIndex];

  if (!isDeleting) {
    // Typing forward
    charIndex++;
    displayedText.value = currentTitle.slice(0, charIndex);

    if (charIndex === currentTitle.length) {
      isDeleting = true;
      timeoutId = setTimeout(tick, HOLD_TIME);
      return;
    }
    timeoutId = setTimeout(tick, TYPE_SPEED);
  } else {
    // Deleting backward
    charIndex--;
    displayedText.value = currentTitle.slice(0, charIndex);

    if (charIndex === 0) {
      isDeleting = false;
      titleIndex = (titleIndex + 1) % titles.length;
      timeoutId = setTimeout(tick, GAP_TIME);
      return;
    }
    timeoutId = setTimeout(tick, DELETE_SPEED);
  }
}

onMounted(() => {
  timeoutId = setTimeout(tick, 500); // small initial delay before it starts
});

onUnmounted(() => {
  clearTimeout(timeoutId);
});
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 100px 4vw 60px;
  position: relative; /* needed so .hero-bg can anchor inside it */
  overflow: hidden; /* keeps orbs from spilling outside the section */
  background-color: var(--color-primary);
}
.hero-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
  pointer-events: none;
}

/* Entrance animation */
.hero-anim {
  opacity: 0;
  transform: translateY(20px);
}

.hero-container.is-loaded .hero-anim {
  animation: heroFadeIn 0.7s ease forwards;
  animation-delay: var(--anim-delay, 0s);
}

@keyframes heroFadeIn {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Status badge */
.status-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background-color: rgba(34, 197, 94, 0.08);
  border: 1px solid rgba(34, 197, 94, 0.3);
  color: #4ade80;
  font-size: 0.8rem;
  font-weight: 500;
  padding: 0.35rem 0.8rem;
  border-radius: 20px;
  margin-bottom: var(--space-sm);
}

.status-dot {
  width: 8px;
  height: 8px;
  background-color: #4ade80;
  border-radius: 50%;
  animation: statusPulse 2s ease-in-out infinite;
}

@keyframes statusPulse {
  0%,
  100% {
    opacity: 1;
    box-shadow: 0 0 0 0 rgba(74, 222, 128, 0.5);
  }
  50% {
    opacity: 0.7;
    box-shadow: 0 0 0 6px rgba(74, 222, 128, 0);
  }
}

/* Scroll indicator */
.scroll-indicator {
  position: absolute;
  bottom: 28px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.25rem;
  color: var(--color-text-muted);
  z-index: 2;
  transition: color 0.2s ease;
}

.scroll-indicator:hover {
  color: var(--color-accent);
}

.scroll-text {
  font-size: 0.7rem;
  letter-spacing: 1.5px;
  text-transform: uppercase;
}

.scroll-chevron {
  font-size: 1.4rem;
  line-height: 1;
  animation: scrollBounce 2s ease-in-out infinite;
}

@keyframes scrollBounce {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(6px);
  }
}

/* Typography rhythm tweaks */
.hero-greeting {
  letter-spacing: 1px;
}

.hero-role {
  margin-bottom: var(--space-sm); /* tightened from --space-md */
}

.hero-photo-wrap {
  transition: transform 1s ease-out; /* smooths the parallax movement */
}

.hero-fade {
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
  z-index: 1;
  pointer-events: none;
}

/* Grid pattern */
.grid-pattern {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(251, 191, 36, 0.06) 1px, transparent 1px),
    linear-gradient(90deg, rgba(251, 191, 36, 0.06) 1px, transparent 1px);
  background-size: 48px 48px;
  mask-image: radial-gradient(circle at center, black 30%, transparent 75%);
  animation: gridPulse 6s ease-in-out infinite;
}

@keyframes gridPulse {
  0%,
  100% {
    opacity: 0.5;
  }
  50% {
    opacity: 1;
  }
}

/* Floating orbs */
.orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(60px);
  opacity: 0.35;
}

.orb-1 {
  width: 320px;
  height: 320px;
  top: 5%;
  left: 8%;
  background: radial-gradient(circle, var(--color-accent), transparent 70%);
  animation: drift1 14s ease-in-out infinite;
}

.orb-2 {
  width: 260px;
  height: 260px;
  bottom: 10%;
  right: 12%;
  background: radial-gradient(circle, var(--color-accent), transparent 70%);
  animation: drift2 18s ease-in-out infinite;
}

.orb-3 {
  width: 200px;
  height: 200px;
  top: 45%;
  left: 45%;
  background: radial-gradient(circle, var(--color-white), transparent 70%);
  opacity: 0.98;
  animation: drift3 20s ease-in-out infinite;
}

@keyframes drift1 {
  0%,
  100% {
    transform: translate(0, 0);
  }
  50% {
    transform: translate(40px, 30px);
  }
}

@keyframes drift2 {
  0%,
  100% {
    transform: translate(0, 0);
  }
  50% {
    transform: translate(-35px, -25px);
  }
}

@keyframes drift3 {
  0%,
  100% {
    transform: translate(0, 0) scale(1);
  }
  50% {
    transform: translate(20px, -40px) scale(1.15);
  }
}

.hero-container {
  max-width: 100%;
  position: relative;
  z-index: 1;
  width: 100%;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1.15fr 0.85fr;
  align-items: center;
  padding: 0 var(--space-lg);
  gap: 4rem;
}

.hero-greeting {
  color: var(--color-text-muted);
  font-size: 1.8rem;
  margin-bottom: var(--space-xs);
}

.hero-name {
  font-size: 6rem;
}

.hero-role {
  font-size: 1.6rem;
  font-weight: 500;
  color: var(--color-white);
  margin-bottom: var(--space-md);
  min-height: 2rem; /* prevents layout jump as text types/deletes */
}

.typed-text {
  font-size: 1.6rem;
  color: var(--color-white);
}
.cursor {
  color: var(--color-accent);
  opacity: 1;
}

.cursor.blink {
  animation: blink 1s step-start infinite;
}

@keyframes blink {
  50% {
    opacity: 0;
  }
}

.hero-desc {
  font-size: 1.8rem;
  max-width: 760px;
}

.hero-actions {
  display: flex;
  align-items: center;
  gap: var(--space-lg);
  margin-bottom: var(--space-lg);
}

.btn-primary {
  background-color: var(--color-accent);
  color: var(--color-primary);
  font-weight: 600;
  padding: 0.75rem 1.5rem;
  border-radius: 6px;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  transition:
    transform 0.2s ease,
    box-shadow 0.2s ease;
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 16px rgba(251, 191, 36, 0.3);
}

.btn-text {
  color: var(--color-text-body);
  font-weight: bold;
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  transition: color 0.2s ease;
  border: 1px solid var(--color-white);
  border-radius: 6px;
  padding: 0.5rem 1rem;
}

.btn-text:hover {
  color: var(--color-accent);
  border-color: var(--color-accent);
  transition:
    color 0.2s ease,
    border-color 0.2s ease;
}

.hero-social {
  display: flex;
  align-items: center;
  gap: var(--space-md);
}

.follow-label {
  font-size: 1.2rem;
  color: var(--color-text-muted);
}

.hero-social a {
  color: var(--color-accent);
  display: flex;
  transition: transform 0.2s ease;
}

.hero-social a:hover {
  transform: translateY(-2px);
}

/* Photo */
.hero-photo-wrap {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

.glow {
  position: absolute;
  width: 320px;
  height: 320px;
  background: radial-gradient(
    circle,
    rgba(224, 174, 62, 0.25),
    transparent 70%
  );
  border-radius: 50%;
  z-index: -1;
}

.hero-photo {
  width: 320px;
  height: 320px;
  object-fit: cover;
  border-radius: 50%;
  border: 3px solid var(--color-accent);
  position: relative;
  z-index: 100;
}

.float-icon {
  position: absolute;
  transform: translateX(-50%, -50%);
  z-index: 2;
  filter: drop-shadow(0 0 6px rgba(0, 0, 0, 0.4));
  animation:
    iconFloatBob 3s ease-in-out infinite,
    iconFadeIn 0.6s ease forwards;
  animation-delay: calc(var(--i, 0) * 0.15s), calc(var(--i, 0) * 0.1s);
  opacity: 0;
  transition:
    transform 0.2s ease-out,
    filter 0.2s ease;
}

.float-icon:hover {
  transform: translate(-50%, -50%) scale(1.25);
  filter: drop-shadow(0 0 12px var(--icon-color));
}

.float-icon svg {
  color: var(--icon-color);
  display: block;
}

@keyframes iconFloatBob {
  0%,
  100% {
    transform: translate(-50%, -50%) translateY(0);
  }
  50% {
    transform: translate(-50%, -50%) translateY(-10px);
  }
}

@keyframes iconFadeIn {
  to {
    opacity: 1;
  }
}

@media (max-width: 900px) {
  .float-icon svg {
    width: 50px;
    height: 50px;
  }
}

@media (max-width: 480px) {
  .float-icon:nth-child(3n) {
    display: none;
  }

  .float-icon svg {
    width: 50px;
    height: 50px;
  }
}

/* .wave-divider {
  position: absolute; */
/* bottom: -1px; prevents a 1px gap/seam from sub-pixel rounding */
/* left: 0; */
/* width: 100%; */
/* line-height: 0; removes inline-svg whitespace gap */
/* z-index: 1; above hero-bg, but content itself sits at z-index 1 too — fine since it's at the very bottom edge */
/* } */

/* .wave-divider svg {
  display: block;
  width: 100%;
  height: 90px;
} */

/* Responsive */

@media (max-width: 900px) {
  .hero-container {
    grid-template-columns: 1fr;
  }

  .hero-photo-wrap {
    order: -1;
  }

  .hero-actions {
    justify-content: center;
  }

  .hero-social {
    justify-content: center;
  }

  /* NEW — scale text and photo down so nothing overflows the viewport */
  .hero-name {
    font-size: 2.75rem;
  }

  .hero-role,
  .typed-text {
    font-size: 1.25rem;
  }

  .hero-desc {
    font-size: 0.95rem;
    max-width: 100%;
  }

  .hero-photo,
  .glow {
    width: 260px;
    height: 260px;
  }

  .float-icon {
    width: 40px;
    height: 40px;
    font-size: 0.65rem;
  }
}

@media (max-width: 480px) {
  .hero-name {
    font-size: 2.1rem;
  }

  .hero-role,
  .typed-text {
    font-size: 1.05rem;
  }

  .hero-photo,
  .glow {
    width: 210px;
    height: 210px;
  }

  .hero-actions {
    flex-direction: column;
    align-items: center;
    gap: var(--space-sm);
  }
}
</style>
