<template>
  <div id="app">
    <!-- <draggable class="flex">
      <sections
        v-for="(item, index) in sectionList"
        :key="index"
        :name="item.name"
        :count="item.taskCount"
      >
      <div>aaa</div>
      </sections>
    </draggable> -->
    <Sample />
    <!-- <Task /> -->
  </div>
</template>

<script>
/* import sections from "./components/Sections.vue";
import Task from "./components/Task.vue";
import draggable from "vuedraggable"; */
import Sample from "./components/Sample.vue";
export default {
  name: "App",
  components: { Sample },
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
  .flex {
    display: flex;
    flex-direction: row;
  }
}
</style>
