<template>
  <section
    class="intro-container"
    :class="{ clear: intro.hero_image_toggle }"
    :style="style"
  >
    <div
      class="introduction"
      :class="{ 'column-adjust': !intro.hero_image_toggle }"
    >
      <div class="project-info">
        <span class="highlight" v-html="client">{{ client }}</span>
        <h1 class="title-project" v-html="intro.page_title" />
        <div class="categories">
          <ul>
            <li
              class="category highlight"
              v-for="(tag, index) in intro.service_tags"
              :key="index"
            >
              <g-link class="tag" :to="formatUrl(tag)">{{
                formatServiceName(tag)
              }}</g-link>
            </li>
          </ul>
        </div>
        <a
          class="highlight url"
          v-if="intro.project_url"
          :href="intro.project_url"
          target="_blank"
          rel="noopener noreferrer"
          >{{ intro.project_url }}</a
        >
      </div>
      <img
        v-if="intro.background_hero_image"
        :src="intro.background_hero_image"
        :class="{
          background: intro.hero_image_toggle,
          'column-img': !intro.hero_image_toggle,
        }"
      />
      <div class="paragraph-block" v-html="intro.intro_paragraph" />
    </div>
    <img
      v-if="intro.client_logo"
      class="client-logo"
      :src="intro.client_logo"
      alt="client logo"
    />
  </section>
</template>

<script>
import formatServiceName from "./utility-funcs/formatServiceName.js"
import formatUrl from "./utility-funcs/formatUrl.js"

export default {
  props: ["intro"],
  methods: {
    formatServiceName,
    formatUrl,
  },
  computed: {
    client() {
      return this.intro.client.toUpperCase()
    },
  },
}
</script>

<style>
.intro-container {
  margin: 2% 0 0;
  color: var(--color-contrast);
  transition: all 300ms ease-in-out;
  background: none;
  height: 700px;
}
.intro-container.clear {
  background: none;
}
.introduction {
  margin: 0 0 2rem;
  font-size: 1.1rem;
  line-height: 1.6rem;
  max-width: 700px;
  transition: all 300ms ease-in-out;
}
.introduction.column-adjust {
  width: 50%;
}
.project-info {
  margin-left: 6rem;
}

.background {
  position: absolute;
  top: -95px;
  left: 0;
  width: 100%;
  height: 900px;
  z-index: -1;
  object-fit: cover;
  background-color: transparent;
}
.column-img {
  position: absolute;
  top: 196px;
  right: 0;
  width: 45%;
  height: auto;
  z-index: 2;
  object-fit: contain;
}
.highlight {
  color: var(--color-highlight);
}
.category.highlight a {
  color: var(--color-highlight);
}
.categories ul {
  list-style: none;
  padding: 0;
  display: flex;
  margin: 1rem 0;
}
.category,
.url {
  font-size: 1rem;
}
.category:nth-child(2) {
  margin-left: 2rem;
}
.paragraph-block {
  margin-left: 6rem;
  font-size: 1.1rem;
  line-height: 1.6rem;
  padding-bottom: 2rem;
  border-bottom: 1px solid var(--color-highlight);
  max-width: 700px;
}
.title-project {
  font-size: 2.75rem;
  line-height: 3.25rem;
  margin: 1rem 0 0;
  max-width: 700px;
}
.client-logo {
  width: auto;
  max-height: 50px;
  margin-left: 6rem;
  margin-top: 1rem;
}
@media (max-width: 1100px) {
  .introduction {
    max-width: 100%;
  }

  .introduction.column-adjust {
    width: 100%;
  }
  .intro-container {
    padding-bottom: 0;
    height: auto;
  }
  .title-project {
    margin: 1rem 0 0;
  }
  .background {
    position: static;
    opacity: 1;
    margin: 2rem 0;
    width: 100%;
    height: auto;
    object-fit: contain;
  }
  .column-img {
    position: relative;
    width: 95%;
    left: 5%;
    top: 0;
  }
  .client-logo {
    display: none;
  }
  .project-info,
  .paragraph-block {
    margin: 0 6rem;
  }
}
@media (max-width: 800px) {
  .project-info,
  .paragraph-block {
    margin: 0 2rem;
  }
  .title {
    font-size: 2rem;
  }
}
@media (min-width: 2000px) {
  .intro-container {
    margin: 5% 0 0;
    height: 900px;
  }
  .background {
    height: 1200px;
  }
}
</style>
