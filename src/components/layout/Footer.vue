<template>
  <footer class="footer">
    <div class="footer-bg">
      <div class="sparkle s1"></div>
      <div class="sparkle s2"></div>
      <div class="sparkle s3"></div>
      <div class="sparkle s4"></div>
      <div class="sparkle s5"></div>
    </div>

    <div class="section-container footer-content">
      <div class="footer-top">
        <div class="footer-brand">
          <div class="footer-logo">
            <span class="logo-mc">MC</span>
            <div class="logo-text">
              <span class="logo-name"
                >MELI <span class="accent-text">CHRISTIAN</span></span
              >
              <span class="logo-tagline">FULL STACK DEVELOPER</span>
            </div>
          </div>
          <p class="footer-desc">
            Building scalable, production-ready web applications with clean
            architecture and attention to detail.
          </p>
        </div>

        <div class="footer-links">
          <h4>Navigate</h4>
          <a href="#home">Home</a>
          <a href="#about">About</a>
          <a href="#skills">Skills</a>
          <a href="#projects">Projects</a>
          <a href="#services">Services</a>
          <a href="#contact">Contact</a>
        </div>

        <div class="footer-links">
          <h4>Connect</h4>
          <a
            href="https://github.com/melichris"
            target="_blank"
            rel="noopener"
            class="connect-link"
          >
            <svg viewBox="0 0 24 24" width="30" height="30">
              <path
                fill="currentColor"
                d="M12 2C6.48 2 2 6.48 2 12c0 4.42 2.87 8.17 6.84 9.5.5.09.66-.22.66-.48v-1.7c-2.78.6-3.37-1.34-3.37-1.34-.46-1.16-1.11-1.47-1.11-1.47-.91-.62.07-.6.07-.6 1 .07 1.53 1.03 1.53 1.03.89 1.52 2.34 1.08 2.91.83.09-.65.35-1.09.63-1.34-2.22-.25-4.56-1.11-4.56-4.94 0-1.09.39-1.98 1.03-2.68-.1-.25-.45-1.27.1-2.65 0 0 .84-.27 2.75 1.03a9.4 9.4 0 0 1 5 0c1.91-1.3 2.75-1.03 2.75-1.03.55 1.38.2 2.4.1 2.65.64.7 1.03 1.59 1.03 2.68 0 3.84-2.35 4.68-4.58 4.93.36.31.68.92.68 1.85v2.75c0 .26.16.57.67.48A10.01 10.01 0 0 0 22 12c0-5.52-4.48-10-10-10z"
              />
            </svg>
            GitHub
          </a>
          <a
            href="https://www.linkedin.com/in/meli-christian/"
            target="_blank"
            rel="noopener"
            class="connect-link"
          >
            <svg viewBox="0 0 24 24" width="30" height="30">
              <path
                fill="currentColor"
                d="M20.45 20.45h-3.56v-5.57c0-1.33-.02-3.04-1.85-3.04-1.85 0-2.14 1.45-2.14 2.94v5.67H9.34V9h3.42v1.56h.05c.48-.9 1.64-1.85 3.38-1.85 3.6 0 4.27 2.37 4.27 5.46v6.28zM5.34 7.43a2.06 2.06 0 1 1 0-4.12 2.06 2.06 0 0 1 0 4.12zM7.12 20.45H3.56V9h3.56v11.45z"
              />
            </svg>
            LinkedIn
          </a>
          <a href="mailto:melichris.work@gmail.com" class="connect-link">
            <svg viewBox="0 0 24 24" width="30" height="30">
              <path
                fill="currentColor"
                d="M20 4H4a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V6a2 2 0 0 0-2-2zm0 4-8 5-8-5V6l8 5 8-5v2z"
              />
            </svg>
            Email
          </a>
        </div>
      </div>

      <div class="footer-bottom">
        <p>© {{ currentYear }} Meli Christian. All rights reserved.</p>
        <button
          class="back-to-top"
          @click="scrollToTop"
          aria-label="Back to top"
        >
          ↑
        </button>
      </div>
    </div>
  </footer>
</template>

<script setup>
const currentYear = new Date().getFullYear();

function scrollToTop() {
  window.scrollTo({ top: 0, behavior: "smooth" });
}
</script>

<style scoped>
.footer {
  position: relative;
  overflow: hidden;
  background-color: var(--color-secondary);
  padding-top: var(--space-xl);
  padding-bottom: var(--space-md);
}

/* Subtle sparkle drift background */
.footer-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
  pointer-events: none;
}

.sparkle {
  position: absolute;
  width: 3px;
  height: 3px;
  background-color: var(--color-accent);
  border-radius: 50%;
  opacity: 0.5;
  animation: sparkleFloat 6s ease-in-out infinite;
}

.connect-link {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  color: var(--color-text-body);
  font-size: 0.88rem;
  transition:
    color 0.2s ease,
    padding-left 0.2s ease;
}

.connect-link:hover {
  color: var(--color-accent);
  padding-left: 4px;
}

.s1 {
  top: 20%;
  left: 10%;
  animation-delay: 0s;
}
.s2 {
  top: 60%;
  left: 25%;
  animation-delay: 1.2s;
}
.s3 {
  top: 30%;
  left: 55%;
  animation-delay: 2.4s;
}
.s4 {
  top: 70%;
  left: 75%;
  animation-delay: 3.6s;
}
.s5 {
  top: 15%;
  left: 85%;
  animation-delay: 4.8s;
}

@keyframes sparkleFloat {
  0%,
  100% {
    transform: translateY(0) scale(1);
    opacity: 0.3;
  }
  50% {
    transform: translateY(-16px) scale(1.6);
    opacity: 0.9;
  }
}

.footer-content {
  position: relative;
  z-index: 1;
}

.footer-top {
  display: grid;
  grid-template-columns: 1.4fr 0.8fr 0.8fr;
  gap: var(--space-xl);
  padding-bottom: var(--space-lg);
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.footer-logo {
  display: flex;
  align-items: center;
  gap: var(--space-xs);
  margin-bottom: var(--space-sm);
}

.logo-mc {
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: var(--color-primary);
  border: 1px solid rgba(251, 191, 36, 0.3);
  border-radius: 8px;
  color: var(--color-accent);
  font-weight: 700;
  font-size: 0.95rem;
}

.logo-text {
  display: flex;
  flex-direction: column;
  line-height: 1.1;
}

.logo-name {
  font-family: var(--font-heading);
  font-weight: 700;
  font-size: 0.95rem;
  color: var(--color-white);
}

.logo-tagline {
  font-size: 0.6rem;
  color: var(--color-text-muted);
  letter-spacing: 1px;
}

.footer-desc {
  color: var(--color-text-body);
  font-size: 0.9rem;
  line-height: 1.6;
  max-width: 320px;
}

.footer-links {
  display: flex;
  flex-direction: column;
  gap: 0.65rem;
}

.footer-links h4 {
  color: var(--color-white);
  font-size: 0.95rem;
  margin-bottom: 0.5rem;
}

.footer-links a {
  color: var(--color-text-body);
  font-size: 0.88rem;
  transition:
    color 0.2s ease,
    padding-left 0.2s ease;
}

.footer-links a:hover {
  color: var(--color-accent);
  padding-left: 4px;
}

.footer-bottom {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: var(--space-md);
}

.footer-bottom p {
  color: var(--color-text-muted);
  font-size: 0.85rem;
}

.back-to-top {
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: var(--color-primary);
  border: 1px solid rgba(251, 191, 36, 0.3);
  border-radius: 50%;
  color: var(--color-accent);
  font-size: 1.1rem;
  transition:
    transform 0.25s ease,
    background-color 0.25s ease;
}

.back-to-top:hover {
  transform: translateY(-4px);
  background-color: var(--color-accent);
  color: var(--color-primary);
}

@media (max-width: 800px) {
  .footer-top {
    grid-template-columns: 1fr;
    gap: var(--space-lg);
  }

  .footer-bottom {
    flex-direction: column;
    gap: var(--space-sm);
    text-align: center;
  }
}
</style>
