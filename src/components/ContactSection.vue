<template>
  <section class="contact">
    <div class="container">
      <div class="contact-content">
        <h2 class="contact-title">Get in touch</h2>
        <p class="contact-description">
          Available for new projects
        </p>
        <div class="contact-links">
          <a href="mailto:your.email@domain.com" class="contact-link">
            Email →
          </a>
          <a href="https://wa.me/62812XXXXXXX" class="contact-link">
            WhatsApp →
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ContactSection'
}
</script>

<style scoped>
.contact {
  background: var(--surface);
  padding: 4rem 0;
  border-top: 1px solid var(--border);
}

.contact-content {
  text-align: center;
  max-width: 500px;
  margin: 0 auto;
}

.contact-title {
  font-size: 2rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  color: var(--text);
}

.contact-description {
  color: var(--text-light);
  margin-bottom: 2rem;
}

.contact-links {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.contact-link {
  color: var(--primary);
  text-decoration: none;
  font-weight: 500;
  padding: 0.75rem 1.5rem;
  border: 1px solid var(--border);
  border-radius: 8px;
  transition: all 0.3s ease;
  background: var(--bg);
}

.contact-link:hover {
  background: var(--primary);
  color: white;
  border-color: var(--primary);
}

@media (max-width: 768px) {
  .contact-links {
    flex-direction: column;
    align-items: center;
  }
  
  .contact-link {
    width: 200px;
    text-align: center;
  }
}
</style>