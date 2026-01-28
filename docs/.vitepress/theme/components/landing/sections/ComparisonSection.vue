<script setup lang="ts"></script>

<template>
  <section class="comparison">
    <div class="section-header">
      <h2>Why Inertia?</h2>
      <p>
        Inertia sits between traditional server-rendered apps and full SPAs.
        Here's how it compares.
      </p>
    </div>

    <div class="comparison-grid">
      <!-- vs Hotwire/Turbo -->
      <div class="comparison-card">
        <h3>Inertia vs Hotwire/Turbo</h3>
        <p class="comparison-intro">
          Both keep you in the Rails monolith. The difference is your view
          layer.
        </p>

        <div class="comparison-table">
          <div class="comparison-row header">
            <span></span>
            <span>Hotwire</span>
            <span>Inertia</span>
          </div>
          <div class="comparison-row">
            <span>View layer</span>
            <span>ERB + Stimulus</span>
            <span>React/Vue/Svelte</span>
          </div>
          <div class="comparison-row">
            <span>Interactivity</span>
            <span>HTML over the wire</span>
            <span>Full component state</span>
          </div>
          <div class="comparison-row">
            <span>JS ecosystem</span>
            <span>Limited</span>
            <span>Full access</span>
          </div>
          <div class="comparison-row">
            <span>Learning curve</span>
            <span>Lower for Rails devs</span>
            <span>Lower for React/Vue devs</span>
          </div>
        </div>

        <p class="comparison-verdict">
          <strong>Choose Hotwire</strong> if you prefer server-rendered HTML and
          minimal JavaScript.<br />
          <strong>Choose Inertia</strong> if you want React/Vue/Svelte
          components with Rails routing.
        </p>
      </div>

      <!-- vs API-first -->
      <div class="comparison-card">
        <h3>Inertia vs API + SPA</h3>
        <p class="comparison-intro">
          Both give you a modern frontend. Inertia removes the API layer.
        </p>

        <div class="comparison-table">
          <div class="comparison-row header">
            <span></span>
            <span>API + SPA</span>
            <span>Inertia</span>
          </div>
          <div class="comparison-row">
            <span>Routing</span>
            <span>Client + server</span>
            <span>Server only</span>
          </div>
          <div class="comparison-row">
            <span>Auth</span>
            <span>Tokens/sessions</span>
            <span>Rails sessions</span>
          </div>
          <div class="comparison-row">
            <span>Data fetching</span>
            <span>API calls in components</span>
            <span>Props from controllers</span>
          </div>
          <div class="comparison-row">
            <span>Deployments</span>
            <span>Two apps</span>
            <span>One app</span>
          </div>
        </div>

        <p class="comparison-verdict">
          <strong>Choose API + SPA</strong> if you need a public API or multiple
          clients.<br />
          <strong>Choose Inertia</strong> if your frontend is for your app only.
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.comparison {
  padding: 6rem 1.5rem;
  max-width: var(--landing-max-width);
  margin: 0 auto;
  position: relative;
  z-index: 1;
}

.section-header {
  text-align: center;
  margin-bottom: 4rem;
}

.section-header h2 {
  font-size: clamp(2rem, 4vw, 2.75rem);
  font-weight: 800;
  margin-bottom: 1rem;
  letter-spacing: -0.03em;
  text-wrap: balance;
}

.section-header p {
  color: var(--landing-text-secondary);
  font-size: 1.125rem;
  max-width: 540px;
  margin: 0 auto;
  line-height: 1.7;
}

.comparison-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
  max-width: 960px;
  margin: 0 auto;
}

.comparison-card {
  padding: 2rem;
  background: var(--landing-card-bg);
  border: 1px solid var(--landing-border);
  border-radius: 1rem;
  backdrop-filter: blur(12px);
}

.comparison-card h3 {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  letter-spacing: -0.02em;
}

.comparison-intro {
  color: var(--landing-text-secondary);
  font-size: 0.9375rem;
  margin-bottom: 1.5rem;
  line-height: 1.6;
}

.comparison-table {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.comparison-row {
  display: grid;
  grid-template-columns: 1.2fr 1fr 1fr;
  gap: 0.75rem;
  padding: 0.625rem 0.75rem;
  background: var(--landing-surface);
  border-radius: 0.5rem;
  font-size: 0.8125rem;
}

.comparison-row.header {
  background: transparent;
  font-weight: 600;
  color: var(--landing-text-muted);
  text-transform: uppercase;
  letter-spacing: 0.05em;
  font-size: 0.6875rem;
  padding-bottom: 0.25rem;
}

.comparison-row span:first-child {
  color: var(--landing-text-secondary);
  font-weight: 500;
}

.comparison-row span:nth-child(2),
.comparison-row span:nth-child(3) {
  color: var(--landing-text-primary);
}

.comparison-verdict {
  font-size: 0.875rem;
  color: var(--landing-text-secondary);
  line-height: 1.7;
  padding-top: 0.5rem;
  border-top: 1px solid var(--landing-border);
}

.comparison-verdict strong {
  color: var(--landing-text-primary);
}

@media (max-width: 960px) {
  .comparison-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 640px) {
  .comparison {
    padding: 3rem 1rem;
  }

  .section-header {
    margin-bottom: 2rem;
  }

  .section-header h2 {
    font-size: 1.75rem;
  }

  .comparison-card {
    padding: 1.25rem;
  }

  .comparison-row {
    font-size: 0.75rem;
    padding: 0.5rem;
    gap: 0.5rem;
  }

  .comparison-row.header {
    font-size: 0.625rem;
  }
}
</style>
