# Meli Christian — Portfolio

A dark-themed, single-page developer portfolio built with Vue 3 and Vite. Features scroll-triggered reveal animations, section-specific animated backgrounds, and a working contact form.

🔗 **Live site:** [add your deployed URL here]

---

## ✨ Features

- **Single-page layout** with smooth-scroll navigation and scroll-spy active link highlighting
- **Animated Hero section** with a cycling typewriter effect and floating tech-stack badges
- **Scroll-triggered reveal animations** across every section, powered by the Intersection Observer API
- **Distinct animated backgrounds per section** — grid + orbs, dot fields, gradient waves, radar pulse rings, and a sparkle-drift footer — all built in pure CSS
- **Glassmorphism service cards** with a hover shine sweep
- **Working contact form** connected to Formspree, with real-time success/error feedback
- **Fully responsive** across mobile, tablet, and desktop breakpoints
- **Accessibility-conscious** — respects `prefers-reduced-motion`, and disables decorative animations on mobile to reduce GPU load

---

## 🛠️ Tech Stack

| Category      | Technology                                       |
| ------------- | ------------------------------------------------ |
| Framework     | Vue 3 (Composition API)                          |
| Build tool    | Vite                                             |
| Language      | JavaScript                                       |
| Styling       | Native CSS (CSS custom properties, no framework) |
| Form handling | Formspree                                        |

No UI framework or CSS library was used intentionally — every layout, animation, and transition in this project is hand-built to demonstrate core CSS and Vue fluency.

---

## 📁 Project Structure

```
src/
├── assets/
│   ├── logo.png
│   └── profile.jpg
├── components/
│   ├── layout/
│   │   ├── NavBar.vue
│   │   └── Footer.vue
│   └── sections/
│       ├── HeroSection.vue
│       ├── AboutSection.vue
│       ├── SkillsSection.vue
│       ├── ProjectsSection.vue
│       ├── ServicesSection.vue
│       └── ContactSection.vue
├── styles/
│   ├── variables.css
│   ├── base.css
│   └── main.css
├── App.vue
└── main.js
```

---

## 🎨 Design System

| Purpose            | Color       | Hex       |
| ------------------ | ----------- | --------- |
| Primary background | Black       | `#111827` |
| Secondary / cards  | Charcoal    | `#374151` |
| Accent             | Gold        | `#FBBF24` |
| Text (body)        | Light Slate | `#D1D5DB` |

Typography: **Poppins** (headings) + **Inter** (body), via Google Fonts.

---

## 🚀 Getting Started

Clone the repo and install dependencies:

```bash
git clone https://github.com/melichris/portfolio.git
cd portfolio
npm install
```

Run the development server:

```bash
npm run dev
```

Build for production:

```bash
npm run build
```

### Environment setup

The contact form uses a [Formspree](https://formspree.io) endpoint. If you fork this project, replace the endpoint in `src/components/sections/ContactSection.vue`:

```js
const FORMSPREE_ENDPOINT = "https://formspree.io/f/your-form-id";
```

---

## 📌 Featured Projects (shown on site)

- **Sentinel Lite** — Vue 3 security monitoring dashboard
- **Driver Hiring Management System** — frontend for a driver hiring platform
- **Face Mask Detection** — computer vision system using OpenCV, TensorFlow, and Keras
- **Exam Surveillance System with AI** — AI-driven exam malpractice detection

---

## 📬 Contact

- **Email:** melichris.work@gmail.com
- **GitHub:** [github.com/melichris](https://github.com/melichris)
- **LinkedIn:** [linkedin.com/in/meli-christian](https://www.linkedin.com/in/meli-christian/)

---

## 📄 License

This project is open for reference and learning purposes. Please don't copy the personal content (name, photos, project descriptions) as your own.
