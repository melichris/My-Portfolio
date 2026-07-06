<template>
  <section id="about" class="about">
    <div class="about-bg"></div>
    <div class="section-container about-grid">
      <div class="about-text">
        <p class="section-label">— About Me</p>
        <h2 class="section-title">Who I Am</h2>
        <p class="about-desc">
          I'm a passionate Full Stack Developer with experience building web
          applications using modern technologies. I enjoy turning ideas into
          real products and solving complex problems with clean code.
        </p>
        <a href="#projects" class="read-more-btn">Read More <span>→</span></a>
      </div>

      <div class="skills-col">
        <p class="section-label">— My Skills</p>
        <div class="skills-grid">
          <div v-for="s in skills" :key="s.name" class="skill-row">
            <span class="skill-icon" :style="{ color: s.color }">
              <svg viewBox="0 0 24 24" width="18" height="18" v-html="s.svg"></svg>
            </span>
            <div class="skill-info">
              <div class="skill-top">
                <span>{{ s.name }}</span><span>{{ s.pct }}%</span>
              </div>
              <div class="skill-bar">
                <div class="skill-fill" :style="{ width: s.pct + '%', background: s.color }"></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const skills = [
  { name: 'HTML5', color: '#E34F26', pct: 95, svg: `<path fill="currentColor" d="M3 2h18l-1.6 18L12 22l-7.4-2z" opacity="0.15"/><path fill="none" stroke="currentColor" stroke-width="1.3" d="M4 4h16l-1.4 15L12 21l-6.6-2z"/><path fill="none" stroke="currentColor" stroke-width="1.3" d="M7 8h10l-.4 4H8l.2 2.5 3.8 1 3.8-1 .3-3.5"/>` },
  { name: 'CSS3', color: '#264DE4', pct: 90, svg: `<path fill="none" stroke="currentColor" stroke-width="1.3" d="M4 4h16l-1.4 15L12 21l-6.6-2z"/><path fill="none" stroke="currentColor" stroke-width="1.3" d="M17 8H7l.3 3h9l-.4 4-3.9 1.2-3.8-1.2-.2-2.2"/>` },
  { name: 'JavaScript', color: '#F7DF1E', pct: 90, svg: `<rect x="2" y="2" width="20" height="20" rx="3" fill="none" stroke="currentColor" stroke-width="1.4"/><text x="12" y="16.5" font-size="9" font-weight="700" text-anchor="middle" fill="currentColor">JS</text>` },
  { name: 'Vue 3', color: '#4FC08D', pct: 90, svg: `<path fill="currentColor" d="M2 3h4l6 10 6-10h4L12 21z"/><path fill="currentColor" opacity="0.6" d="M6 3h3.2L12 7.8 14.8 3H18l-6 10z"/>` },
  { name: 'React', color: '#61DAFB', pct: 80, svg: `<ellipse cx="12" cy="12" rx="10" ry="4.2" fill="none" stroke="currentColor" stroke-width="1.4"/><ellipse cx="12" cy="12" rx="10" ry="4.2" fill="none" stroke="currentColor" stroke-width="1.4" transform="rotate(60 12 12)"/><ellipse cx="12" cy="12" rx="10" ry="4.2" fill="none" stroke="currentColor" stroke-width="1.4" transform="rotate(120 12 12)"/><circle cx="12" cy="12" r="1.8" fill="currentColor"/>` },
  { name: 'PHP', color: '#777BB4', pct: 75, svg: `<ellipse cx="12" cy="12" rx="10" ry="6" fill="none" stroke="currentColor" stroke-width="1.4"/><text x="12" y="15" font-size="6.5" font-weight="700" text-anchor="middle" fill="currentColor" font-style="italic">php</text>` },
  { name: 'Node.js', color: '#68A063', pct: 85, svg: `<path fill="none" stroke="currentColor" stroke-width="1.5" d="M12 2 21 7v10l-9 5-9-5V7z"/>` },
  { name: 'Python', color: '#3776AB', pct: 75, svg: `<path fill="currentColor" d="M12 2c-3 0-5 1-5 4v2h5v1H4c-2 0-3 2-3 5s1 5 3 5h2v-3c0-2 2-4 4-4h4c2 0 3-1 3-3V6c0-2-2-4-5-4zm-2 3a1 1 0 110 2 1 1 0 010-2z"/><path fill="currentColor" opacity="0.55" d="M12 22c3 0 5-1 5-4v-2h-5v-1h8c2 0 3-2 3-5s-1-5-3-5h-2v3c0 2-2 4-4 4H10c-2 0-3 1-3 3v3c0 2 2 4 5 4zm2-3a1 1 0 110-2 1 1 0 010 2z"/>` },
  { name: 'MySQL', color: '#4479A1', pct: 80, svg: `<ellipse cx="12" cy="6" rx="8" ry="3" fill="none" stroke="currentColor" stroke-width="1.4"/><path fill="none" stroke="currentColor" stroke-width="1.4" d="M4 6v12c0 1.7 3.6 3 8 3s8-1.3 8-3V6"/><path fill="none" stroke="currentColor" stroke-width="1.2" d="M4 12c0 1.7 3.6 3 8 3s8-1.3 8-3"/>` },
]
</script>

<style scoped>
.about {
  position: relative;
  overflow: hidden;
  background-color: var(--color-primary);
}

.about-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
  pointer-events: none;
  background: linear-gradient(120deg, rgba(251, 191, 36, 0.12) 0%, rgba(55, 65, 81, 0.35) 25%, rgba(251, 191, 36, 0.10) 50%, rgba(55, 65, 81, 0.35) 75%, rgba(251, 191, 36, 0.12) 100%);
  background-size: 300% 300%;
  animation: waveShift 16s ease-in-out infinite;
}

@keyframes waveShift {
  0% {
    background-position: 0% 50%
  }

  50% {
    background-position: 100% 50%
  }

  100% {
    background-position: 0% 50%
  }
}

.about-grid {
  position: relative;
  z-index: 1;
  display: grid;
  grid-template-columns: 0.85fr 1.15fr;
  gap: var(--space-xl);
  align-items: start;
}

.section-label {
  color: var(--color-accent);
  font-weight: 600;
  font-size: 0.9rem;
  letter-spacing: 1px;
  margin-bottom: var(--space-xs);
}

.section-title {
  font-size: 2.2rem;
  margin-bottom: var(--space-md);
}

.about-desc {
  color: var(--color-text-body);
  line-height: 1.7;
  max-width: 480px;
  margin-bottom: var(--space-lg);
}

.read-more-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  border: 1px solid rgba(251, 191, 36, 0.4);
  color: var(--color-accent);
  padding: 0.6rem 1.4rem;
  border-radius: 6px;
  font-weight: 600;
  font-size: 0.9rem;
  transition: background-color 0.2s ease, color 0.2s ease, transform 0.2s ease;
}

.read-more-btn:hover {
  background-color: var(--color-accent);
  color: var(--color-primary);
  transform: translateX(3px);
}

.skills-col {
  border-left: 1px solid rgba(255, 255, 255, 0.08);
  padding-left: var(--space-xl);
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--space-md) var(--space-lg);
}

.skill-row {
  display: flex;
  align-items: center;
  gap: 0.6rem;
}

.skill-icon {
  width: 30px;
  height: 30px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background: transparent;
  border-radius: 6px;
  font-size: 0.75rem;
  font-weight: 700;
  transition: transform 0.25s ease;
}

.skill-row:hover .skill-icon {
  transform: translateY(-3px) scale(1.08);
}

.skill-info {
  flex: 1;
  min-width: 0;
}

.skill-top {
  display: flex;
  justify-content: space-between;
  font-size: 0.8rem;
  color: var(--color-text-body);
  margin-bottom: 4px;
}

.skill-bar {
  height: 4px;
  background: rgba(255, 255, 255, 0.08);
  border-radius: 4px;
  overflow: hidden;
}

.skill-fill {
  height: 100%;
  border-radius: 4px;
  transition: width 1s ease;
}

@media (max-width: 900px) {
  .about-grid {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .about-text {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .about-desc {
    margin-left: auto;
    margin-right: auto;
  }

  .skills-col {
    border-left: none;
    padding-left: 0;
    border-top: 1px solid rgba(255, 255, 255, 0.08);
    padding-top: var(--space-lg);
    text-align: left;
  }

  .skills-grid {
    grid-template-columns: repeat(2, 1fr);
    justify-items: center;
  }

  .skill-row {
    max-width: 220px;
  }
}
</style>
