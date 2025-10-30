<template>
  <div id="app" :class="{ 'dark': darkMode }">
    <header class="header">
      <div class="nav">
        <div class="logo">Portfolio</div>
        <button @click="toggleDarkMode" class="theme-btn" aria-label="Toggle dark mode">
          <div class="theme-switch">
            <div class="switch-handle" :class="{ 'dark': darkMode }"></div>
          </div>
        </button>
      </div>
    </header>

    <main class="main">
      <!-- Hero -->
      <section class="hero">
        <h1>Full-Stack Developer</h1>
        <p>Based in Bali, Indonesia</p>
      </section>

      <!-- Projects -->
      <section class="projects">
        <h2>Projects</h2>
        <div class="project-list">
          <div 
            class="project-item fade-in" 
            v-for="(project, index) in projects" 
            :key="project.id"
            :style="{ '--delay': index * 0.1 + 's' }"
          >
            <a :href="project.liveUrl" target="_blank" rel="noopener noreferrer" class="project-link">
              <div class="project-header">
                <h3 class="project-domain">{{ project.domain }}</h3>
                <span class="live-indicator">
                  <span class="live-dot"></span>
                  Live
                </span>
              </div>
              <p class="project-desc">{{ project.description }}</p>
              <div class="tech-tags">
                <span v-for="tech in project.tech" :key="tech" class="tech-tag">
                  {{ tech }}
                </span>
              </div>
            </a>
          </div>
        </div>
      </section>

      <!-- Contact -->
      <section class="contact">
        <p>Get in touch: 
          <a href="mailto:kuswiono.2013@gmail.com">Email</a> • 
          <a href="https://wa.me/62882006194560">WhatsApp</a>
        </p>
      </section>
    </main>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      darkMode: false,
      projects: [
        {
          id: 1,
          domain: "urbancart-final.vercel.app",
          description: "Modern e-commerce platform with full shopping cart & checkout",
          tech: ["Next.js", "TypeScript", "Tailwind CSS", "Vercel"],
          liveUrl: "https://urbancart-final.vercel.app"
        },
        {
          id: 2,
          domain: "bubossdrinkery.com",
          description: "E-commerce with payment integration",
          tech: ["Laravel", "Custom Frontend", "WhatsApp API"],
          liveUrl: "https://www.bubossdrinkery.com/home"
        },
        {
          id: 3,
          domain: "paradisespaonbene.com", 
          description: "Booking system with scheduling",
          tech: ["Laravel", "Custom Frontend", "Booking"],
          liveUrl: "https://paradisespaonbene.com/"
        },
        {
          id: 4,
          domain: "glowing.co.id",
          description: "Membership platform",
          tech: ["WordPress", "Membership", "SEO"],
          liveUrl: "https://glowing.co.id/"
        }
      ]
    }
  },
  methods: {
    toggleDarkMode() {
      this.darkMode = !this.darkMode;
    }
  }
}
</script>

<style>
:root {
  --bg: #ffffff;
  --surface: #f8f9fa;
  --text: #212529;
  --text-light: #6c757d;
  --border: #dee2e6;
  --primary: #3b82f6;
  --live: #10b981;
}

.dark {
  --bg: #0f172a;
  --surface: #1e293b;
  --text: #f8f9fa;
  --text-light: #adb5bd;
  --border: #495057;
  --primary: #4dabf7;
  --live: #34d399;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: var(--bg);
  color: var(--text);
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  line-height: 1.4;
  transition: background 0.3s, color 0.3s;
}

/* Header */
.header {
  padding: 1rem;
  border-bottom: 1px solid var(--border);
}

.nav {
  max-width: 600px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-weight: 600;
  font-size: 1.1rem;
}

/* Theme Switch */
.theme-btn {
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
  border-radius: 50%;
  transition: background 0.3s;
}

.theme-switch {
  width: 44px;
  height: 24px;
  background: var(--surface);
  border: 2px solid var(--border);
  border-radius: 24px;
  position: relative;
  transition: all 0.3s ease;
}

.switch-handle {
  position: absolute;
  top: 2px;
  left: 2px;
  width: 16px;
  height: 16px;
  background: var(--primary);
  border-radius: 50%;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
}

.switch-handle.dark {
  transform: translateX(20px);
  background: #f59e0b;
}

/* Main Content */
.main {
  max-width: 600px;
  margin: 0 auto;
  padding: 1.5rem 1rem;
}

/* Hero */
.hero {
  text-align: center;
  margin-bottom: 2rem;
}

.hero h1 {
  font-size: 1.5rem;
  margin-bottom: 0.3rem;
}

.hero p {
  color: var(--text-light);
  font-size: 0.9rem;
}

/* Projects */
.projects h2 {
  margin-bottom: 1rem;
  font-size: 1.3rem;
}

.project-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.project-item {
  background: var(--surface);
  border-radius: 6px;
  border: 1px solid var(--border);
  transition: all 0.3s ease;
}

.project-link {
  display: block;
  padding: 1rem;
  text-decoration: none;
  color: inherit;
}

.project-item:hover {
  border-color: var(--primary);
  transform: translateY(-3px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
}

.project-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.5rem;
}

.project-domain {
  font-size: 1.1rem;
  font-weight: 600;
  color: var(--primary);
}

.live-indicator {
  color: var(--text-light);
  font-size: 0.8rem;
  display: flex;
  align-items: center;
  gap: 0.3rem;
}

.live-dot {
  width: 6px;
  height: 6px;
  background: var(--live);
  border-radius: 50%;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0% {
    transform: scale(0.8);
    opacity: 1;
  }
  50% {
    transform: scale(1.2);
    opacity: 0.7;
  }
  100% {
    transform: scale(0.8);
    opacity: 1;
  }
}

.project-desc {
  color: var(--text-light);
  font-size: 0.9rem;
  margin-bottom: 0.5rem;
}

.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.3rem;
}

.tech-tag {
  background: var(--primary);
  color: white;
  padding: 0.2rem 0.6rem;
  border-radius: 12px;
  font-size: 0.75rem;
  font-weight: 500;
}

/* Contact */
.contact {
  margin-top: 2rem;
  text-align: center;
  padding-top: 1rem;
  border-top: 1px solid var(--border);
}

.contact p {
  color: var(--text-light);
  font-size: 0.9rem;
}

.contact a {
  color: var(--primary);
  text-decoration: none;
}

.contact a:hover {
  text-decoration: underline;
}

/* Fade-in Animation */
.fade-in {
  opacity: 0;
  transform: translateY(10px);
  animation: fadeInUp 0.6s ease forwards;
  animation-delay: var(--delay, 0s);
}

@keyframes fadeInUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Responsive */
@media (max-width: 768px) {
  .main {
    padding: 1rem;
  }

  .hero h1 {
    font-size: 1.3rem;
  }

  .project-link {
    padding: 0.8rem;
  }
}
</style>