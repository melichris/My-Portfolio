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
            <span class="skill-icon" :style="{ color: s.color }">{{ s.abbr }}</span>
            <div class="skill-info">
              <div class="skill-top">
                <span>{{ s.name }}</span><span>{{ s.pct }}%</span>
              </div>
              <div class="skill-bar"><div class="skill-fill" :style="{ width: s.pct + '%', background: s.color }"></div></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const skills = [
  { name: 'HTML5', abbr: '5', color: '#E34F26', pct: 95 },
  { name: 'CSS3', abbr: '3', color: '#264DE4', pct: 90 },
  { name: 'JavaScript', abbr: 'JS', color: '#F7DF1E', pct: 90 },
  { name: 'Vue 3', abbr: 'V', color: '#4FC08D', pct: 90 },
  { name: 'React', abbr: '⚛', color: '#61DAFB', pct: 80 },
  { name: 'PHP', abbr: 'P', color: '#777BB4', pct: 75 },
  { name: 'Node.js', abbr: 'N', color: '#68A063', pct: 85 },
  { name: 'Python', abbr: 'Py', color: '#3776AB', pct: 75 },
  { name: 'MySQL', abbr: 'My', color: '#4479A1', pct: 80 },
]
</script>

<style scoped>
.about { position: relative; overflow: hidden; background-color: var(--color-primary); }
.about-bg {
  position: absolute; inset: 0; z-index: 0; pointer-events: none;
  background: linear-gradient(120deg, rgba(251,191,36,0.12) 0%, rgba(55,65,81,0.35) 25%, rgba(251,191,36,0.10) 50%, rgba(55,65,81,0.35) 75%, rgba(251,191,36,0.12) 100%);
  background-size: 300% 300%;
  animation: waveShift 16s ease-in-out infinite;
}
@keyframes waveShift { 0%{background-position:0% 50%} 50%{background-position:100% 50%} 100%{background-position:0% 50%} }

.about-grid { position: relative; z-index: 1; display: grid; grid-template-columns: 0.85fr 1.15fr; gap: var(--space-xl); align-items: start; }

.section-label { color: var(--color-accent); font-weight: 600; font-size: 0.9rem; letter-spacing: 1px; margin-bottom: var(--space-xs); }
.section-title { font-size: 2.2rem; margin-bottom: var(--space-md); }
.about-desc { color: var(--color-text-body); line-height: 1.7; max-width: 480px; margin-bottom: var(--space-lg); }

.read-more-btn {
  display: inline-flex; align-items: center; gap: 0.5rem;
  border: 1px solid rgba(251,191,36,0.4); color: var(--color-accent);
  padding: 0.6rem 1.4rem; border-radius: 6px; font-weight: 600; font-size: 0.9rem;
  transition: background-color 0.2s ease, color 0.2s ease, transform 0.2s ease;
}
.read-more-btn:hover { background-color: var(--color-accent); color: var(--color-primary); transform: translateX(3px); }

.skills-col { border-left: 1px solid rgba(255,255,255,0.08); padding-left: var(--space-xl); }
.skills-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: var(--space-md) var(--space-lg); }

.skill-row { display: flex; align-items: center; gap: 0.6rem; }
.skill-icon {
  width: 30px; height: 30px; flex-shrink: 0; display: flex; align-items: center; justify-content: center;
  background: var(--color-secondary); border-radius: 6px; font-size: 0.75rem; font-weight: 700;
  transition: transform 0.25s ease;
}
.skill-row:hover .skill-icon { transform: translateY(-3px) scale(1.08); }

.skill-info { flex: 1; min-width: 0; }
.skill-top { display: flex; justify-content: space-between; font-size: 0.8rem; color: var(--color-text-body); margin-bottom: 4px; }
.skill-bar { height: 4px; background: rgba(255,255,255,0.08); border-radius: 4px; overflow: hidden; }
.skill-fill { height: 100%; border-radius: 4px; transition: width 1s ease; }

@media (max-width: 900px) {
  .about-grid { grid-template-columns: 1fr; }
  .skills-col { border-left: none; padding-left: 0; border-top: 1px solid rgba(255,255,255,0.08); padding-top: var(--space-lg); }
  .skills-grid { grid-template-columns: repeat(2, 1fr); }
}
</style>
