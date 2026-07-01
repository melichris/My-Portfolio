<template>
  <section id="contact" class="contact" ref="sectionRef">
    <div class="contact-fade-in"></div>

    <div class="contact-bg">
      <div class="pulse-ring ring-1"></div>
      <div class="pulse-ring ring-2"></div>
      <div class="pulse-ring ring-3"></div>
    </div>

    <div class="section-container">
      <p class="section-label reveal">— Contact</p>
      <h2 class="section-title reveal" style="--delay: 0.1s">
        Let's Build Something
        <span class="wobble-text">Great</span>
      </h2>
      <p class="contact-intro reveal" style="--delay: 0.2s">
        Available for freelance projects and full-time opportunities. Reach out
        and let's talk.
      </p>

      <div class="contact-layout">
        <!-- Left: direct info -->
        <div class="contact-info reveal" style="--delay: 0.3s">
          <div class="info-item">
            <span class="info-icon">✉</span>
            <div>
              <p class="info-label">Email</p>
              <a href="mailto:youremail@example.com" class="info-value"
                >youremail@example.com</a
              >
            </div>
          </div>
          <div class="info-item">
            <span class="info-icon">☎</span>
            <div>
              <p class="info-label">Phone</p>
              <a href="tel:+237000000000" class="info-value"
                >+237 XXX XXX XXX</a
              >
            </div>
          </div>
          <div class="info-item">
            <span class="info-icon">⚲</span>
            <div>
              <p class="info-label">Location</p>
              <p class="info-value">Douala, Cameroon</p>
            </div>
          </div>

          <div class="info-socials">
            <a
              href="#"
              target="_blank"
              rel="noopener"
              aria-label="GitHub"
              class="social-circle"
              >GH</a
            >
            <a
              href="#"
              target="_blank"
              rel="noopener"
              aria-label="LinkedIn"
              class="social-circle"
              >Li</a
            >
            <a
              href="#"
              target="_blank"
              rel="noopener"
              aria-label="Twitter"
              class="social-circle"
              >Tw</a
            >
          </div>
        </div>

        <!-- Right: form -->
        <form
          class="contact-form reveal"
          style="--delay: 0.4s"
          @submit.prevent="handleSubmit"
        >
          <div class="form-row">
            <input
              type="text"
              v-model="form.name"
              placeholder="Your Name"
              required
            />
            <input
              type="email"
              v-model="form.email"
              placeholder="Your Email"
              required
            />
          </div>
          <input
            type="text"
            v-model="form.subject"
            placeholder="Subject"
            required
          />
          <textarea
            v-model="form.message"
            placeholder="Your Message"
            rows="5"
            required
          ></textarea>
          <button type="submit" class="submit-btn">
            Send Message <span class="arrow">→</span>
          </button>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive, onMounted, onUnmounted } from "vue";

const form = reactive({ name: "", email: "", subject: "", message: "" });

function handleSubmit() {
  // Placeholder — wire up to an email service (e.g. Formspree, EmailJS) later
  console.log("Form submitted:", form);
  alert(
    "Message sent! (connect this to a real email service before deploying)",
  );
}

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
.contact {
  position: relative;
  overflow: hidden;
  background-color: var(--color-primary);
  padding-top: var(--space-xl);
  padding-bottom: var(--space-xl);
}

.contact-fade-in {
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

/* Radar pulse-ring background — new pattern, distinct from all prior sections */
.contact-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
  pointer-events: none;
  display: flex;
  align-items: center;
  justify-content: center;
}

.pulse-ring {
  position: absolute;
  border: 1px solid rgba(251, 191, 36, 0.25);
  border-radius: 50%;
  right: 5%;
  top: 30%;
}

.ring-1 {
  width: 200px;
  height: 200px;
  animation: pulseRing 4s ease-out infinite;
}
.ring-2 {
  width: 200px;
  height: 200px;
  animation: pulseRing 4s ease-out infinite 1.3s;
}
.ring-3 {
  width: 200px;
  height: 200px;
  animation: pulseRing 4s ease-out infinite 2.6s;
}

@keyframes pulseRing {
  0% {
    transform: scale(0.6);
    opacity: 0.6;
  }
  100% {
    transform: scale(2.4);
    opacity: 0;
  }
}

.section-container {
  position: relative;
  z-index: 1;
}

.contact-intro {
  color: var(--color-text-body);
  max-width: 560px;
  margin-bottom: var(--space-xl);
}

/* Wobbling accent text — continuous, subtle rotation wobble */
.wobble-text {
  display: inline-block;
  color: var(--color-accent);
  animation: wobble 2.8s ease-in-out infinite;
  transform-origin: 50% 100%;
}

@keyframes wobble {
  0%,
  100% {
    transform: rotate(0deg);
  }
  25% {
    transform: rotate(-3deg);
  }
  75% {
    transform: rotate(3deg);
  }
}

/* Layout */
.contact-layout {
  display: grid;
  grid-template-columns: 0.8fr 1.2fr;
  gap: var(--space-xl);
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: var(--space-lg);
}

.info-item {
  display: flex;
  align-items: flex-start;
  gap: var(--space-sm);
}

.info-icon {
  width: 44px;
  height: 44px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: var(--color-secondary);
  border: 1px solid rgba(251, 191, 36, 0.25);
  border-radius: 10px;
  color: var(--color-accent);
  font-size: 1.1rem;
}

.info-label {
  font-size: 0.8rem;
  color: var(--color-text-muted);
}

.info-value {
  color: var(--color-white);
  font-weight: 500;
  font-size: 0.95rem;
}

.info-socials {
  display: flex;
  gap: 0.75rem;
  margin-top: var(--space-sm);
}

.social-circle {
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid rgba(251, 191, 36, 0.3);
  border-radius: 50%;
  color: var(--color-accent);
  font-size: 0.75rem;
  font-weight: 700;
  transition:
    background-color 0.25s ease,
    color 0.25s ease,
    transform 0.25s ease;
}

.social-circle:hover {
  background-color: var(--color-accent);
  color: var(--color-primary);
  transform: translateY(-3px);
}

/* Form */
.contact-form {
  display: flex;
  flex-direction: column;
  gap: var(--space-sm);
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--space-sm);
}

.contact-form input,
.contact-form textarea {
  background-color: var(--color-secondary);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 8px;
  padding: 0.85rem 1rem;
  color: var(--color-white);
  font-family: var(--font-body);
  font-size: 0.95rem;
  resize: vertical;
  transition:
    border-color 0.25s ease,
    box-shadow 0.25s ease;
}

.contact-form input::placeholder,
.contact-form textarea::placeholder {
  color: var(--color-text-muted);
}

.contact-form input:focus,
.contact-form textarea:focus {
  outline: none;
  border-color: var(--color-accent);
  box-shadow: 0 0 0 3px rgba(251, 191, 36, 0.12);
}

.submit-btn {
  align-self: flex-start;
  background-color: var(--color-accent);
  color: var(--color-primary);
  font-weight: 600;
  padding: 0.85rem 1.75rem;
  border-radius: 8px;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  transition:
    transform 0.2s ease,
    box-shadow 0.2s ease;
}

.submit-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(251, 191, 36, 0.25);
}

/* Reveal */
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

@media (max-width: 900px) {
  .contact-layout {
    grid-template-columns: 1fr;
  }

  .form-row {
    grid-template-columns: 1fr;
  }
}
</style>
