<template>
  <section class="results margin">
    <div class="three-column">
      <div class="roi" v-html="addSuperscript(resultsObj.column_one)"></div>
      <div class="roi" v-html="addSuperscript(resultsObj.column_two)"></div>
      <div class="roi" v-html="addSuperscript(resultsObj.column_three)"></div>
    </div>
  </section>
</template>

<script>
export default {
  props: ["resultsObj"],
  methods: {
    addSuperscript(htmlString) {
      return htmlString.replace(/%/g, "<sup>%</sup>")
    },
  },
}
</script>

<style>
.results {
  margin-top: 1rem;
  margin-bottom: 10rem;
}
.three-column {
  display: flex;
  justify-content: space-around;
  width: 1200px;
  margin: 0 auto;
}
.roi {
  color: var(--color-highlight);
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: left;
  min-width: 33.3%;
}
.roi > h1,
.roi > h2,
.roi > h3,
.roi > h4,
.roi > h5,
.roi > h6 {
  font-family: "DM Sans", sans-serif;
  font-weight: normal;
  font-size: 5rem;
  margin: 0;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.roi > p {
  color: var(--color-contrast);
  margin-top: 0;
}
sup {
  font-size: 2.75rem;
}

@media (max-width: 1200px) {
  .three-column {
    flex-direction: column;
    width: auto;
  }
  .results {
    margin-top: 1rem;
    margin-bottom: 2rem;
  }
  sup {
    font-size: 1.5rem;
  }
}
</style>
