<template>
  <section class="hero">
    <div class="container">
      <div class="hero-content">
        <h1 class="hero-title">
          Full-Stack
          <span class="gradient-text">Developer</span>
        </h1>
        <p class="hero-description">
          Building modern web applications with Laravel & Vue.js
        </p>
        <div class="hero-location">
          <span class="location-dot">●</span>
          Based in Bali, Indonesia
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'HeroSection'
}
</script>

<style scoped>
.hero {
  padding: 8rem 0 4rem;
  background: var(--bg);
  border-bottom: 1px solid var(--border);
}

.hero-content {
  max-width: 600px;
  text-align: center;
  margin: 0 auto;
}

.hero-title {
  font-size: 3rem;
  font-weight: 600;
  margin-bottom: 1rem;
  line-height: 1.1;
  color: var(--text);
}

.gradient-text {
  background: linear-gradient(135deg, var(--gradient-from), var(--gradient-to));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-description {
  font-size: 1.25rem;
  color: var(--text-light);
  margin-bottom: 2rem;
}

.hero-location {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--text-light);
  font-size: 1rem;
}

.location-dot {
  color: #10b981;
  font-size: 0.5rem;
}

@media (max-width: 768px) {
  .hero {
    padding: 6rem 0 3rem;
  }
  
  .hero-title {
    font-size: 2.25rem;
  }
  
  .hero-description {
    font-size: 1.1rem;
  }
}
</style>