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
              <a href="mailto:melichris.work@gmail.com" class="info-value"
                >melichris.work@gmail.com</a
              >
            </div>
          </div>
          <div class="info-item">
            <span class="info-icon">☎</span>
            <div>
              <p class="info-label">Phone</p>
              <a href="tel:+237653369392" class="info-value"
                >+237 653 369 392</a
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
              href="https://github.com/melichris"
              target="_blank"
              rel="noopener"
              aria-label="GitHub"
              class="social-circle"
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
              class="social-circle"
            >
              <svg viewBox="0 0 24 24" width="30" height="30">
                <path
                  fill="currentColor"
                  d="M20.45 20.45h-3.56v-5.57c0-1.33-.02-3.04-1.85-3.04-1.85 0-2.14 1.45-2.14 2.94v5.67H9.34V9h3.42v1.56h.05c.48-.9 1.64-1.85 3.38-1.85 3.6 0 4.27 2.37 4.27 5.46v6.28zM5.34 7.43a2.06 2.06 0 1 1 0-4.12 2.06 2.06 0 0 1 0 4.12zM7.12 20.45H3.56V9h3.56v11.45z"
                />
              </svg>
            </a>
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

          <button type="submit" class="submit-btn" :disabled="isSubmitting">
            {{ isSubmitting ? "Sending..." : "Send Message" }}
            <span class="arrow" v-if="!isSubmitting">→</span>
          </button>

          <p v-if="submitStatus === 'success'" class="form-feedback success">
            ✓ Message sent successfully — I'll get back to you soon!
          </p>
          <p v-if="submitStatus === 'error'" class="form-feedback error">
            ✕ Something went wrong. Please try again or email me directly.
          </p>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive, onMounted, onUnmounted } from "vue";

const form = reactive({ name: "", email: "", subject: "", message: "" });
const isSubmitting = ref(false);
const submitStatus = ref(null); // null | 'success' | 'error'

const FORMSPREE_ENDPOINT = "https://formspree.io/f/mvzjwljb"; // ← replace with your real endpoint

async function handleSubmit() {
  isSubmitting.value = true;
  submitStatus.value = null;

  try {
    const response = await fetch(FORMSPREE_ENDPOINT, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        Accept: "application/json",
      },
      body: JSON.stringify({
        name: form.name,
        email: form.email,
        subject: form.subject,
        message: form.message,
      }),
    });

    if (response.ok) {
      submitStatus.value = "success";
      form.name = "";
      form.email = "";
      form.subject = "";
      form.message = "";
    } else {
      submitStatus.value = "error";
    }
  } catch (err) {
    submitStatus.value = "error";
  } finally {
    isSubmitting.value = false;
  }
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

.form-feedback {
  font-size: 0.9rem;
  padding: 0.75rem 1rem;
  border-radius: 8px;
  margin-top: 0.25rem;
}

.form-feedback.success {
  background-color: rgba(34, 197, 94, 0.1);
  border: 1px solid rgba(34, 197, 94, 0.3);
  color: #4ade80;
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
