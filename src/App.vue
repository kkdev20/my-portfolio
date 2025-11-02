<template>
  <div id="app">
    <!-- Scroll Progress Bar -->
    <div class="scroll-progress" :style="{ width: scrollProgress + '%' }"></div>
    
    <header class="header">
      <div class="nav">
        <div class="logo">
          <svg class="logo-icon" width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M3 3h18v18H3V3zm16 16V5H5v14h14zM7 7h10v2H7V7zm0 4h10v2H7v-2zm0 4h7v2H7v-2z" fill="currentColor"/>
          </svg>
          <span>Portfolio</span>
        </div>
        <div class="header-controls">
          <button @click="toggleLanguage" class="lang-btn" aria-label="Toggle language">
            <span class="globe-icon">🌐</span>
            <span>{{ language === 'id' ? 'EN' : 'ID' }}</span>
          </button>
          <button @click="toggleDarkMode" class="theme-btn" aria-label="Toggle dark mode">
            <div class="theme-switch">
              <div class="switch-handle" :class="{ 'dark': darkMode }"></div>
            </div>
          </button>
        </div>
      </div>
    </header>

    <main class="main">
      <!-- Hero -->
      <section class="hero">
        <h1><span class="gradient-text">Full-Stack</span> Developer</h1>
        <p>{{ t.location }}</p>
      </section>

      <!-- About -->
      <section class="about">
        <p class="about-text">
          {{ t.about }}
        </p>
        <p class="about-skills">Skills: Frontend • Backend • UI/UX • SEO • Laravel • Next.js • WordPress • TypeScript</p>
      </section>

      <!-- Projects -->
      <section class="projects">
        <h2>{{ t.projects }}</h2>
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
        <p>{{ t.getInTouch }} 
          <a href="mailto:kuswiono.2013@gmail.com">Email</a> • 
          <a href="https://wa.me/62882006194560" class="whatsapp-link">
            <span class="whatsapp-text">WhatsApp</span>
            <span class="whatsapp-number">+62 882-0061-94560</span>
          </a>
        </p>
      </section>
    </main>

    <!-- Scroll to Top Button -->
    <button 
      @click="scrollToTop" 
      :class="['scroll-top-btn', { 'show': showScrollTop }]"
      aria-label="Scroll to top"
    >
      <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
        <line x1="12" y1="19" x2="12" y2="5"></line>
        <polyline points="5 12 12 5 19 12"></polyline>
      </svg>
    </button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      language: 'id',
      darkMode: false,
      scrollProgress: 0,
      showScrollTop: false,
      translations: {
        id: {
          location: "Berdasarkan di Bali, Indonesia 🇮🇩",
          about: "Web developer berpengalaman 5+ tahun dalam membangun aplikasi web modern, responsif, dan user-friendly dengan teknologi terkini.",
          projects: "Proyek",
          getInTouch: "Hubungi saya: "
        },
        en: {
          location: "Based in Bali, Indonesia 🇮🇩",
          about: "Web developer with 5+ years of experience building modern, responsive, and user-friendly web applications with cutting-edge technologies.",
          projects: "Projects",
          getInTouch: "Get in touch: "
        }
      },
      projectsId: [
        {
          id: 1,
          domain: "urbancart.wistack.site",
          description: "Platform e-commerce modern dengan keranjang belanja & checkout lengkap",
          tech: ["Next.js", "TypeScript", "Tailwind CSS", "Vercel"],
          liveUrl: "https://urbancart.wistack.site"
        },
        {
          id: 2,
          domain: "saas.wistack.site",
          description: "Landing page SaaS modern untuk platform kolaborasi tim",
          tech: ["Next.js", "TypeScript", "Tailwind CSS", "Vercel"],
          liveUrl: "https://saas.wistack.site"
        },
        {
          id: 3,
          domain: "travel.wistack.site",
          description: "Website pariwisata Bali dengan sistem booking",
          tech: ["Next.js", "TypeScript", "Tailwind CSS", "Vercel"],
          liveUrl: "https://travel.wistack.site"
        },
        {
          id: 4,
          domain: "paradisespaonbene.com", 
          description: "Sistem booking dengan penjadwalan",
          tech: ["Laravel", "Custom Frontend", "Booking", "SEO"],
          liveUrl: "https://paradisespaonbene.com/"
        },
        {
          id: 5,
          domain: "glowing.co.id",
          description: "Platform membership",
          tech: ["WordPress", "Membership", "SEO"],
          liveUrl: "https://glowing.co.id/"
        }
      ],
      projectsEn: [
        {
          id: 1,
          domain: "urbancart.wistack.site",
          description: "Modern e-commerce platform with full shopping cart & checkout",
          tech: ["Next.js", "TypeScript", "Tailwind CSS", "Vercel"],
          liveUrl: "https://urbancart.wistack.site"
        },
        {
          id: 2,
          domain: "saas.wistack.site",
          description: "Modern SaaS landing page for team collaboration platform",
          tech: ["Next.js", "TypeScript", "Tailwind CSS", "Vercel"],
          liveUrl: "https://saas.wistack.site"
        },
        {
          id: 3,
          domain: "travel.wistack.site",
          description: "Travel website for Bali tourism with booking system",
          tech: ["Next.js", "TypeScript", "Tailwind CSS", "Vercel"],
          liveUrl: "https://travel.wistack.site"
        },
        {
          id: 4,
          domain: "paradisespaonbene.com", 
          description: "Booking system with scheduling",
          tech: ["Laravel", "Custom Frontend", "Booking", "SEO"],
          liveUrl: "https://paradisespaonbene.com/"
        },
        {
          id: 5,
          domain: "glowing.co.id",
          description: "Membership platform",
          tech: ["WordPress", "Membership", "SEO"],
          liveUrl: "https://glowing.co.id/"
        }
      ]
    }
  },
  computed: {
    t() {
      return this.translations[this.language];
    },
    projects() {
      return this.language === 'id' ? this.projectsId : this.projectsEn;
    }
  },
  methods: {
    toggleLanguage() {
      this.language = this.language === 'id' ? 'en' : 'id';
      localStorage.setItem('language', this.language);
    },
    toggleDarkMode() {
      this.darkMode = !this.darkMode;
      // Apply dark class to html element for global CSS variables
      if (this.darkMode) {
        document.documentElement.classList.add('dark');
        localStorage.setItem('darkMode', 'true');
      } else {
        document.documentElement.classList.remove('dark');
        localStorage.setItem('darkMode', 'false');
      }
    },
    handleScroll() {
      // Calculate scroll progress
      const windowHeight = document.documentElement.scrollHeight - document.documentElement.clientHeight;
      const scrolled = window.pageYOffset;
      this.scrollProgress = (scrolled / windowHeight) * 100;
      
      // Show/hide scroll to top button
      this.showScrollTop = scrolled > 300;
    },
    scrollToTop() {
      window.scrollTo({
        top: 0,
        behavior: 'smooth'
      });
    }
  },
  mounted() {
    // Initialize language
    const savedLanguage = localStorage.getItem('language');
    if (savedLanguage) {
      this.language = savedLanguage;
    }

    // Initialize dark mode state from localStorage or system preference
    const savedDarkMode = localStorage.getItem('darkMode');
    if (savedDarkMode !== null) {
      this.darkMode = savedDarkMode === 'true';
    } else {
      // Check system preference
      const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
      this.darkMode = prefersDark;
    }
    
    // Apply initial state
    if (this.darkMode) {
      document.documentElement.classList.add('dark');
    }

    // Add smooth scroll behavior
    document.documentElement.style.scrollBehavior = 'smooth';
    
    // Add scroll event listener
    window.addEventListener('scroll', this.handleScroll);
    this.handleScroll(); // Initial check
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
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
  --gradient-1: 59, 130, 246; /* blue */
  --gradient-2: 139, 92, 246; /* purple */
  --gradient-3: 236, 72, 153; /* pink */
  --grid-color: 0, 0, 0;
  --surface-rgb: 248, 249, 250;
  --primary-rgb: 59, 130, 246;
}

html.dark,
html.dark body {
  --bg: #0f172a;
  --surface: #1e293b;
  --text: #f8f9fa;
  --text-light: #adb5bd;
  --border: #495057;
  --primary: #4dabf7;
  --live: #34d399;
  --gradient-1: 77, 171, 247; /* light blue */
  --gradient-2: 139, 92, 246; /* purple */
  --gradient-3: 34, 211, 153; /* teal */
  --grid-color: 255, 255, 255;
  --surface-rgb: 30, 41, 59;
  --primary-rgb: 77, 171, 247;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: var(--bg);
  background-image: 
    radial-gradient(at 40% 20%, rgba(var(--gradient-1), 0.1) 0px, transparent 50%),
    radial-gradient(at 80% 80%, rgba(var(--gradient-2), 0.08) 0px, transparent 50%),
    radial-gradient(at 0% 50%, rgba(var(--gradient-3), 0.05) 0px, transparent 50%);
  background-attachment: fixed;
  color: var(--text);
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  line-height: 1.4;
  transition: background 0.3s, color 0.3s, background-image 0.3s;
  position: relative;
  min-height: 100vh;
}

body::before {
  content: '';
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: 
    linear-gradient(90deg, transparent 79px, rgba(var(--grid-color), 0.03) 81px, rgba(var(--grid-color), 0.03) 82px, transparent 84px),
    linear-gradient(rgba(var(--grid-color), 0.03) 79px, transparent 81px, transparent 82px, rgba(var(--grid-color), 0.03) 84px);
  background-size: 80px 80px;
  pointer-events: none;
  z-index: 0;
}

/* Scroll Progress Bar */
.scroll-progress {
  position: fixed;
  top: 0;
  left: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--primary), #8b5cf6, #ec4899);
  z-index: 9999;
  transition: width 0.1s ease;
  box-shadow: 0 0 10px rgba(59, 130, 246, 0.5);
}

html.dark .scroll-progress {
  box-shadow: 0 0 10px rgba(77, 171, 247, 0.5);
}

/* Scroll to Top Button */
.scroll-top-btn {
  position: fixed;
  bottom: 2rem;
  right: 2rem;
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: var(--primary);
  color: white;
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
  z-index: 1000;
  opacity: 0;
  transform: translateY(20px) scale(0.8);
  pointer-events: none;
}

.scroll-top-btn.show {
  opacity: 1;
  transform: translateY(0) scale(1);
  pointer-events: all;
}

.scroll-top-btn:hover {
  transform: scale(1.1) translateY(-2px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.2);
  background: var(--primary);
}

.scroll-top-btn:active {
  transform: scale(0.95);
}

.scroll-top-btn svg {
  width: 20px;
  height: 20px;
}

/* Header */
.header {
  padding: 1rem;
  border-bottom: 1px solid var(--border);
  background: rgba(var(--surface-rgb), 0.8);
  backdrop-filter: blur(10px);
  position: relative;
  z-index: 10;
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
  display: flex;
  align-items: center;
  gap: 0.5rem;
  transition: transform 0.3s ease;
}

.logo:hover {
  transform: scale(1.05);
}

.logo-icon {
  width: 24px;
  height: 24px;
  transition: transform 0.3s ease;
  animation: pulse-icon 2s ease-in-out infinite;
}

.logo:hover .logo-icon {
  transform: rotate(5deg);
}

@keyframes pulse-icon {
  0%, 100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.1);
  }
}

.header-controls {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

/* Language Switch */
.lang-btn {
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem 0.75rem;
  border-radius: 6px;
  transition: background 0.3s;
  font-weight: 600;
  font-size: 0.85rem;
  color: var(--text);
  display: flex;
  align-items: center;
  gap: 0.3rem;
}

.lang-btn:hover {
  background: var(--surface);
}

.globe-icon {
  font-size: 1rem;
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
  position: relative;
  z-index: 1;
}

/* Hero */
.hero {
  text-align: center;
  margin-bottom: 0.5rem;
  padding: 0.5rem 0;
}

.hero h1 {
  font-size: 1.5rem;
  margin-bottom: 0.15rem;
}

.hero p {
  color: var(--text-light);
  font-size: 0.9rem;
}

.hero-description {
  margin-top: 0.5rem;
  opacity: 0.8;
}

.gradient-text {
  background: linear-gradient(135deg, var(--primary), #8b5cf6, #ec4899);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: gradient-shift 3s ease infinite;
  background-size: 200% 200%;
}

@keyframes gradient-shift {
  0%, 100% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
}

/* About */
.about {
  margin-bottom: 1rem;
  margin-top: -0.5rem;
  text-align: center;
}

.about-text {
  color: var(--text-light);
  font-size: 0.9rem;
  line-height: 1.5;
  margin-bottom: 0.3rem;
}

.about-skills {
  color: var(--text-light);
  font-size: 0.8rem;
  line-height: 1.5;
}

/* Projects */
.projects h2 {
  margin-bottom: 1rem;
  font-size: 1.3rem;
  text-align: center;
}

.project-list {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
}

.project-item {
  background: rgba(var(--surface-rgb), 0.9);
  backdrop-filter: blur(10px);
  border-radius: 6px;
  border: 1px solid var(--border);
  transition: all 0.3s ease;
  position: relative;
  z-index: 1;
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
  transition: all 0.3s ease;
}

.contact a:hover {
  text-decoration: underline;
}

.whatsapp-link {
  position: relative;
  display: inline-block;
  padding: 0.2rem 0.5rem;
  border-radius: 6px;
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.whatsapp-link:hover {
  background: rgba(37, 211, 102, 0.1);
  transform: scale(1.05);
  box-shadow: 0 4px 12px rgba(37, 211, 102, 0.2);
}

.whatsapp-text {
  display: inline-block;
  color: var(--primary);
  transition: all 0.3s ease;
  position: relative;
}

.whatsapp-link:hover .whatsapp-text {
  color: #25d366;
  font-weight: 600;
  animation: bounce 0.5s ease;
}

.whatsapp-number {
  display: inline-block;
  opacity: 0;
  transform: translateX(-10px);
  margin-left: 0.5rem;
  color: #25d366;
  font-weight: 500;
  font-size: 0.85rem;
  transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
  position: absolute;
  left: 100%;
  white-space: nowrap;
  background: rgba(37, 211, 102, 0.15);
  border: 1px solid rgba(37, 211, 102, 0.3);
  padding: 0.2rem 0.6rem;
  border-radius: 4px;
  pointer-events: none;
}

.whatsapp-link:hover .whatsapp-number {
  opacity: 1;
  transform: translateX(8px);
  animation: slideIn 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
}

@keyframes bounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-4px);
  }
}

@keyframes slideIn {
  0% {
    opacity: 0;
    transform: translateX(-10px) scale(0.8);
  }
  100% {
    opacity: 1;
    transform: translateX(8px) scale(1);
  }
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

  .project-list {
    grid-template-columns: 1fr;
  }

  .project-link {
    padding: 0.8rem;
  }

  .whatsapp-number {
    position: static;
    opacity: 0;
    transform: translateX(-10px);
    margin-left: 0.5rem;
    margin-top: 0;
  }

  .whatsapp-link:hover .whatsapp-number {
    opacity: 1;
    transform: translateX(8px);
  }

  .contact p {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
    gap: 0.3rem;
  }


  .scroll-top-btn {
    bottom: 1rem;
    right: 1rem;
    width: 44px;
    height: 44px;
  }
}
</style>