<template>
  <header class="navbar" :class="{ scrolled: isScrolled }">
    <div class="navbar-container">
      <!-- Logo -->
      <a href="#home" class="navbar-logo">
        <img src="../../assets/logo1.png" alt="logo" class="logo-img" />
        <div class="logo-text">
          <span class="logo-name"
            >MELI <span class="accent-text">CHRISTIAN</span></span
          >
          <span class="logo-tagline">FULL STACK DEVELOPER</span>
        </div>
      </a>

      <!-- Desktop Nav Links -->
      <nav class="navbar-links" :class="{ open: menuOpen }">
        <a
          v-for="link in links"
          :key="link.id"
          :href="`#${link.id}`"
          class="nav-link"
          :class="{ active: activeSection === link.id }"
          @click="closeMenu"
        >
          {{ link.label }}
        </a>
      </nav>

      <!-- Hire Me CTA (desktop) -->
      <a href="#contact" class="hire-me-btn">Hire Me</a>

      <!-- Mobile menu toggle -->
      <button
        class="menu-toggle"
        @click="menuOpen = !menuOpen"
        aria-label="Toggle menu"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const links = [
  { id: "home", label: "Home" },
  { id: "about", label: "About" },
  { id: "skills", label: "Skills" },
  { id: "projects", label: "Projects" },
  { id: "services", label: "Services" },
  { id: "contact", label: "Contact" },
];

const menuOpen = ref(false);
const isScrolled = ref(false);
const activeSection = ref("home");

function closeMenu() {
  menuOpen.value = false;
}

function handleScroll() {
  isScrolled.value = window.scrollY > 20;

  // Determine which section is currently in view
  const sections = links
    .map((l) => document.getElementById(l.id))
    .filter(Boolean);
  for (const section of sections) {
    const rect = section.getBoundingClientRect();
    if (rect.top <= 120 && rect.bottom >= 120) {
      activeSection.value = section.id;
      break;
    }
  }
}

onMounted(() => window.addEventListener("scroll", handleScroll));
onUnmounted(() => window.removeEventListener("scroll", handleScroll));
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  background-color: transparent;
  transition:
    background-color 0.3s ease,
    box-shadow 0.3s ease;
}

.navbar.scrolled {
  background-color: var(--color-primary);
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.4);
}

.navbar-container {
  max-width: 90%;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: var(--space-sm) 4vw;
}

.navbar-logo {
  display: flex;
  align-items: center;
  gap: var(--space-xs);
}

.logo-img {
  height: 60px;
  width: auto;
}

.logo-text {
  display: flex;
  flex-direction: column;
  line-height: 1.1;
}

.logo-name {
  font-family: var(--font-heading);
  font-weight: 700;
  font-size: 1.45rem;
  color: var(--color-white);
  letter-spacing: 0.5px;
}

.logo-tagline {
  font-size: 0.65rem;
  color: var(--color-text-muted);
  letter-spacing: 1px;
}

.navbar-links {
  display: flex;
  gap: var(--space-lg);
}

.nav-link {
  font-size: 1rem;
  font-weight: bold;
  color: var(--color-text-body);
  padding-bottom: 4px;
  border-bottom: 2px solid transparent;
  transition:
    color 0.2s ease,
    border-color 0.2s ease;
}

.nav-link:hover {
  color: var(--color-white);
}

.nav-link.active {
  color: var(--color-accent);
  border-bottom-color: var(--color-accent);
}

.hire-me-btn {
  border: 1.5px solid var(--color-accent);
  color: var(--color-accent);
  padding: 0.5rem 1.25rem;
  border-radius: 6px;
  font-size: 0.9rem;
  font-weight: 600;
  transition:
    background-color 0.2s ease,
    color 0.2s ease;
}

.hire-me-btn:hover {
  background-color: var(--color-accent);
  color: var(--color-primary);
}

.menu-toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
}

.menu-toggle span {
  width: 24px;
  height: 2px;
  background-color: var(--color-white);
}

/* Mobile */
@media (max-width: 768px) {
  .navbar-links {
    position: fixed;
    top: 64px;
    left: 0;
    width: 100%;
    background-color: var(--color-secondary);
    flex-direction: column;
    align-items: center;
    gap: var(--space-md);
    padding: var(--space-md) 0;
    transform: translateY(-150%);
    transition: transform 0.3s ease;
  }

  .navbar-links.open {
    transform: translateY(0);
  }

  .hire-me-btn {
    display: none;
  }

  .menu-toggle {
    display: flex;
  }
}
</style>
