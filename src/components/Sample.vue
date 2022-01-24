<template>
  <div>
    <draggable class="flex">
      <div v-for="(item, index) in list" :key="index" class="section-container">
        <HeaderInput
          :index="index"
          @delete="deleteSection($event)"
          @newTask="createTask($event)"
        />
        <draggable :list="item" group="people">
          <div v-for="(element, i) in item" :key="i">
            <Task
              :itemID="element.id"
              :taskState="element.status"
              @setTaskStatus="
                setStatus({ index: index, type: $event, item: i })
              "
            />
          </div>
        </draggable>
      </div>
      <div class="new-section-container">
        <button class="new-btn" @click="newSection()">New Section</button>
      </div>
    </draggable>
  </div>
</template>
<script>
import draggable from "vuedraggable";
import HeaderInput from "./HeaderInput.vue";
import Task from "./Task.vue";

export default {
  name: "two-lists",
  display: "Two Lists",
  order: 1,
  components: {
    draggable,
    Task,
    HeaderInput,
  },
  data() {
    return {
      list: [
        [
          { status: "active", id: 1 },
          { status: "confirmed", id: 2 },
          { status: "cancelled", id: 3 },
          { status: "onhold", id: 4 },
        ],

        [
          { status: "pending", id: 5 },
          { status: "onhold", id: 6 },
          { status: "completed", id: 7 },
        ],

        [{ status: "active", id: 8 }],
      ],
    };
  },
  mounted() {},
  methods: {
    newSection() {
      this.list.push([]);
    },
    deleteSection(val) {
      this.list.splice(val, 1);
    },
    createTask(val) {
      this.list[val].push({ status: "active" });
    },
    setStatus(val) {
      console.log(val);
      this.list[val.index][val.item].status = val.type;
    },
  },
};
</script>
<style lang="scss">
.flex {
  display: flex;
  flex-direction: row;
  min-height: calc(100vh - 6rem);
}
.section-container {
  width: 360px;
  height: auto;
  min-height: calc(100vh - 6rem);
  box-shadow: 0px 0px 2px rgba(118, 96, 126, 0.45);
  padding: 1rem;
  display: flex;
  margin-right: 1rem;
  border-radius: 5px;
  flex-direction: column;
  background: rgba(251, 251, 251, 0.5);
}
.new-section-container {
  display: flex;
  height: 60px;
  align-items: center;
  margin-right: 3rem;

  .new-btn {
    padding: 0.8rem 1rem;
    outline: none;
    border: none;
    border-radius: 10px;
    background-color: #03a9f4;
    color: white;
    font-size: 16px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
  }
}
</style>
