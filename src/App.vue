<template>
  <NavBar />
  <main>
    <!-- sections go here -->
    <HeroSection />
    <AboutSection />
    <SkillsSection />
    <!-- <ProjectsSection /> -->
    <!-- <ServicesSection /> -->
    <!-- <ContactSection /> -->
  </main>
</template>

<script setup>
import NavBar from "./components/layout/NavBar.vue";
import HeroSection from "./components/sections/HeroSection.vue";
import AboutSection from "./components/sections/AboutSection.vue";
import SkillsSection from "./components/sections/SkillsSection.vue";
// import ProjectsSection from "./components/sections/ProjectsSection.vue";
// import ServicesSection from "./components/sections/ServicesSection.vue";
// import ContactSection from "./components/sections/ContactSection.vue";
</script>
