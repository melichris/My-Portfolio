<template>
  <section id="about" class="about">
    <div class="section-container about-grid">
      <!-- Left: heading + text -->
      <div class="about-text">
        <p class="section-label">— About Me</p>
        <h2 class="section-title">Who I Am</h2>
        <p class="about-desc">
          I'm a Full Stack Developer with hands-on experience building
          production-ready web applications using Vue 3, Node.js, and modern
          tooling. I've worked on Docker-based infrastructure and ERP deployment
          in a professional setting, alongside independently built projects
          covering authentication systems, real-time dashboards, and e-commerce
          platforms.
        </p>
        <p class="about-desc">
          I care about clean architecture, readable code, and building things
          that actually hold up in production — not just tutorials that work
          once and break under real use.
        </p>

        <div class="about-stats">
          <div class="stat">
            <span class="stat-number">13+</span>
            <span class="stat-label">Major Projects</span>
          </div>
          <div class="stat">
            <span class="stat-number">5+</span>
            <span class="stat-label">Professional Role</span>
          </div>
          <div class="stat">
            <span class="stat-number">100%</span>
            <span class="stat-label">Committed to Quality</span>
          </div>
        </div>
      </div>

      <!-- Right: highlight card -->
      <div class="about-highlight">
        <div class="highlight-card">
          <h3>What I Bring</h3>
          <ul class="highlight-list">
            <li>
              <span class="check">✓</span>
              Full lifecycle experience — from Docker infrastructure to deployed
              UI
            </li>
            <li>
              <span class="check">✓</span>
              Comfortable owning a feature end-to-end: auth, state, API, styling
            </li>
            <li>
              <span class="check">✓</span>
              Strong Vue 3 + Composition API fluency across multiple real
              projects
            </li>
            <li>
              <span class="check">✓</span>
              Detail-oriented — I sweat things like spacing, consistency, and
              error states
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup></script>

<style scoped>
.about {
  background-color: var(--color-primary);
}

.about-grid {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: var(--space-xl);
  align-items: start;
}

.section-label {
  color: var(--color-accent);
  font-weight: 600;
  font-size: 1rem;
  letter-spacing: 1px;
  margin-bottom: var(--space-xs);
}

.section-title {
  font-size: 2.8rem;
  margin-bottom: var(--space-md);
}

.about-desc {
  color: var(--color-text-body);
  margin-bottom: var(--space-sm);
  max-width: 620px;
  line-height: 1.7;
}

.about-stats {
  display: flex;
  gap: var(--space-xl);
  margin-top: var(--space-lg);
}

.stat {
  display: flex;
  flex-direction: column;
}

.stat-number {
  font-family: var(--font-heading);
  font-size: 2rem;
  font-weight: 700;
  color: var(--color-accent);
}

.stat-label {
  font-size: 0.85rem;
  color: var(--color-text-muted);
  margin-top: 0.25rem;
}

.highlight-card {
  background-color: var(--color-secondary);
  border: 1px solid rgba(251, 191, 36, 0.2);
  border-radius: 12px;
  padding: var(--space-lg);
}

.highlight-card h3 {
  font-size: 1.3rem;
  margin-bottom: var(--space-md);
}

.highlight-list {
  display: flex;
  flex-direction: column;
  gap: var(--space-md);
}

.highlight-list li {
  display: flex;
  gap: 0.75rem;
  color: var(--color-text-body);
  font-size: 0.95rem;
  line-height: 1.6;
}

.check {
  color: var(--color-accent);
  font-weight: 700;
  flex-shrink: 0;
}

/* Responsive */
@media (max-width: 900px) {
  .about-grid {
    grid-template-columns: 1fr;
  }

  .about-stats {
    flex-wrap: wrap;
    gap: var(--space-lg);
  }
}
</style>
