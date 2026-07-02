<template>
  <section id="home" class="hero">
    <!-- Motion background layer -->
    <div class="hero-bg">
      <div class="grid-pattern"></div>
      <div class="orb orb-1"></div>
      <div class="orb orb-2"></div>
      <div class="orb orb-3"></div>
    </div>

    <div class="hero-container">
      <!-- Text content -->
      <div class="hero-content">
        <p class="hero-greeting">Hello, I'm</p>
        <h1 class="hero-name">
          Meli <span class="accent-text">Christian</span>
        </h1>
        <h2 class="hero-role">
          <span class="typed-text">{{ displayedText }}</span
          ><span class="cursor blink">|</span>
        </h2>
        <p class="hero-desc">
          I build scalable and high-performance web applications that deliver
          great user experiences.
        </p>

        <div class="hero-actions">
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
      <div class="hero-photo-wrap">
        <div class="glow"></div>
        <img
          src="../../assets/profile.png"
          alt="Meli Christian"
          class="hero-photo"
        />

        <div class="float-icon icon-1"><span>JS</span></div>
        <div class="float-icon icon-2"><span>TS</span></div>
        <div class="float-icon icon-3"><span>React</span></div>
        <div class="float-icon icon-4"><span>NOde</span></div>
        <!-- <div class="float-icon icon-5"><span>HTML</span></div>
        <div class="float-icon icon-6"><span>DB</span></div>
        <div class="float-icon icon-7"><span>CSS</span></div> -->
      </div>
    </div>

    <div class="hero-fade"></div>

    <!-- Wave divider -->
    <!-- <div class="wave-divider">
      <svg
        viewBox="0 0 1440 120"
        preserveAspectRatio="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <defs>
          <linearGradient id="waveGradient" x1="0%" y1="0%" x2="0%" y2="100%">
            <stop offset="0%" stop-color="#111827" />
            <stop offset="100%" stop-color="#374151" />
          </linearGradient>
        </defs>
        <path
          d="M0,64 C240,120 480,0 720,32 C960,64 1200,112 1440,48 L1440,120 L0,120 Z"
          fill="url(#waveGradient)"
        />
      </svg>
    </div> -->
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

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
  background: radial-gradient(circle, #ffffff, transparent 70%);
  opacity: 0.08;
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
  font-weight: 500;
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  transition: color 0.2s ease;
}

.btn-text:hover {
  color: var(--color-accent);
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
  width: 520px;
  height: 520px;
  background: radial-gradient(
    circle,
    rgba(251, 191, 36, 0.25),
    transparent 70%
  );
  border-radius: 50%;
  z-index: 0;
}

.hero-photo {
  width: 520px;
  height: 520px;
  object-fit: cover;
  border-radius: 50%;
  border: 3px solid var(--color-accent);
  position: relative;
  z-index: 1;
}

.float-icon {
  position: absolute;
  width: 48px;
  height: 48px;
  background-color: var(--color-secondary);
  border: 1px solid var(--color-accent);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  font-size: 0.75rem;
  color: var(--color-accent);
  z-index: 2;
  animation: float 4s ease-in-out infinite;
}

.icon-1 {
  top: 10%;
  left: 0;
  animation-delay: 0s;
}
.icon-2 {
  top: 15%;
  right: 0;
  animation-delay: 1s;
}
.icon-3 {
  bottom: 15%;
  left: 5%;
  animation-delay: 2s;
}
.icon-4 {
  bottom: 10%;
  right: 5%;
  animation-delay: 1.5s;
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-12px);
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
