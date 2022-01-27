<template>
  <div id="app">
    <Sections />
  </div>
</template>

<script>
import Sections from "./components/Sections.vue";
export default {
  name: "App",
  components: { Sections },
  data() {
    return {
      sectionList: [
        { name: "Section 1", id: 1, taskCount: 3 },
        { name: "Section 2", id: 2, taskCount: 4 },
        { name: "Section 3", id: 3, taskCount: 2 },
      ],
    };
  },
  methods: {},
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500&display=swap");
#app {
  width: auto;
  height: auto;
  display: flex;
  font-family: "IBM Plex Sans", sans-serif;
  padding: 3rem;
}
</style>
