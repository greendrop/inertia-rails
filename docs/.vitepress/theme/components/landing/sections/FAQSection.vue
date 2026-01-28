<script setup lang="ts">
import { ref } from 'vue'

const faqs = [
  {
    question: 'Do I need to build an API?',
    answer:
      'No. Inertia eliminates the need for a separate API. Your Rails controllers pass data directly to your React, Vue, or Svelte components as props. If you later need a public API, you can add one alongside Inertia.',
  },
  {
    question: 'Can I use my existing Rails authentication?',
    answer:
      'Yes. Inertia works with standard Rails session-based authentication. Devise, Clearance, Sorcery, or custom auth—it all works. No tokens or OAuth flows required for your own frontend.',
  },
  {
    question: 'How does it handle form validation?',
    answer:
      'Validation errors from your Rails models flow automatically to your components. Use the useForm hook to access errors by field name, just like Rails form helpers. No manual error state management.',
  },
  {
    question: 'What about SEO and server-side rendering?',
    answer:
      'Inertia supports SSR out of the box. Your React, Vue, or Svelte components render on the server for fast first paint and full SEO compatibility. The starter kits include SSR configuration.',
  },
  {
    question: 'Can I migrate incrementally from a Rails app?',
    answer:
      'Yes. Inertia can coexist with traditional Rails views. Convert pages one at a time—your ERB views and Inertia components can live side by side during migration.',
  },
  {
    question: 'How does Inertia compare to Turbo/Hotwire?',
    answer:
      'Both keep you in the Rails monolith. Hotwire sends HTML over the wire with Stimulus for interactivity. Inertia uses React, Vue, or Svelte as your view layer with full component state. Choose based on your team\'s frontend preferences.',
  },
]

const openIndex = ref<number | null>(null)

const toggle = (index: number) => {
  openIndex.value = openIndex.value === index ? null : index
}
</script>

<template>
  <section class="faq">
    <div class="section-header">
      <h2>Frequently asked questions</h2>
      <p>Common questions about using Inertia with Rails.</p>
    </div>

    <div class="faq-list">
      <div
        v-for="(faq, index) in faqs"
        :key="index"
        class="faq-item"
        :class="{ open: openIndex === index }"
      >
        <button class="faq-question" @click="toggle(index)">
          <span>{{ faq.question }}</span>
          <span class="faq-icon" aria-hidden="true">
            <svg
              width="20"
              height="20"
              viewBox="0 0 20 20"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M5 7.5L10 12.5L15 7.5"
                stroke="currentColor"
                stroke-width="1.5"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>
          </span>
        </button>
        <div class="faq-answer">
          <p>{{ faq.answer }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.faq {
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

.faq-list {
  max-width: 720px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.faq-item {
  background: var(--landing-card-bg);
  border: 1px solid var(--landing-border);
  border-radius: 0.75rem;
  overflow: hidden;
  transition: border-color 0.2s ease;
}

.faq-item:hover {
  border-color: var(--landing-hover-border);
}

.faq-item.open {
  border-color: var(--landing-primary);
}

.faq-question {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  padding: 1.25rem 1.5rem;
  background: none;
  border: none;
  cursor: pointer;
  text-align: left;
  font-size: 1rem;
  font-weight: 600;
  color: var(--landing-text-primary);
  transition: color 0.2s ease;
}

.faq-question:hover {
  color: var(--landing-primary);
}

.faq-icon {
  flex-shrink: 0;
  color: var(--landing-text-muted);
  transition:
    transform 0.3s var(--ease-out-expo),
    color 0.2s ease;
}

.faq-item.open .faq-icon {
  transform: rotate(180deg);
  color: var(--landing-primary);
}

.faq-answer {
  display: grid;
  grid-template-rows: 0fr;
  transition: grid-template-rows 0.3s var(--ease-out-expo);
}

.faq-item.open .faq-answer {
  grid-template-rows: 1fr;
}

.faq-answer p {
  overflow: hidden;
  padding: 0 1.5rem;
  margin: 0;
  font-size: 0.9375rem;
  line-height: 1.7;
  color: var(--landing-text-secondary);
  transition: padding 0.3s var(--ease-out-expo);
}

.faq-item.open .faq-answer p {
  padding: 0 1.5rem 1.25rem;
}

@media (max-width: 640px) {
  .faq {
    padding: 3rem 1rem;
  }

  .section-header {
    margin-bottom: 2rem;
  }

  .section-header h2 {
    font-size: 1.75rem;
  }

  .faq-question {
    padding: 1rem 1.25rem;
    font-size: 0.9375rem;
  }

  .faq-answer p {
    padding: 0 1.25rem;
    font-size: 0.875rem;
  }

  .faq-item.open .faq-answer p {
    padding: 0 1.25rem 1rem;
  }
}
</style>
