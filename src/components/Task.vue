<template>
  <div class="tasks" draggable="true">
    <div class="task-status">
      <span class="status" :class="taskState">{{ taskState }}</span>
      <div class="set-status-icon">
        <svg
          width="14"
          height="14"
          viewBox="0 0 100 100"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
          @click="statusDisplay = !statusDisplay"
        >
          <path
            d="M40.625 18.75C40.625 16.2636 41.6127 13.879 43.3709 12.1209C45.129 10.3627 47.5136 9.375 50 9.375C52.4864 9.375 54.871 10.3627 56.6291 12.1209C58.3873 13.879 59.375 16.2636 59.375 18.75C59.375 21.2364 58.3873 23.621 56.6291 25.3791C54.871 27.1373 52.4864 28.125 50 28.125C47.5136 28.125 45.129 27.1373 43.3709 25.3791C41.6127 23.621 40.625 21.2364 40.625 18.75ZM40.625 50C40.625 47.5136 41.6127 45.129 43.3709 43.3709C45.129 41.6127 47.5136 40.625 50 40.625C52.4864 40.625 54.871 41.6127 56.6291 43.3709C58.3873 45.129 59.375 47.5136 59.375 50C59.375 52.4864 58.3873 54.871 56.6291 56.6291C54.871 58.3873 52.4864 59.375 50 59.375C47.5136 59.375 45.129 58.3873 43.3709 56.6291C41.6127 54.871 40.625 52.4864 40.625 50ZM40.625 81.25C40.625 78.7636 41.6127 76.379 43.3709 74.6209C45.129 72.8627 47.5136 71.875 50 71.875C52.4864 71.875 54.871 72.8627 56.6291 74.6209C58.3873 76.379 59.375 78.7636 59.375 81.25C59.375 83.7364 58.3873 86.121 56.6291 87.8791C54.871 89.6373 52.4864 90.625 50 90.625C47.5136 90.625 45.129 89.6373 43.3709 87.8791C41.6127 86.121 40.625 83.7364 40.625 81.25Z"
            fill="#BDBDBD"
          />
        </svg>
        <div class="set-status" v-if="statusDisplay">
          <div class="status-item" @click="setStatus('active')">
            <span class="active status-circle"></span>
            <span>Active</span>
          </div>
          <div class="status-item" @click="setStatus('confirmed')">
            <span class="confirmed status-circle"></span>
            <span>Confirmed</span>
          </div>
          <div class="status-item" @click="setStatus('onhold')">
            <span class="onhold status-circle"></span>
            <span>On Hold</span>
          </div>
          <div class="status-item" @click="setStatus('pending')">
            <span class="pending status-circle"></span>
            <span>Pending</span>
          </div>
          <div class="status-item" @click="setStatus('cancelled')">
            <span class="cancelled status-circle"></span>
            <span>Cancelled</span>
          </div>
          <div class="status-item" @click="setStatus('completed')">
            <span class="completed status-circle"></span>
            <span>Completed</span>
          </div>
        </div>
      </div>
    </div>
    <div class="task-content">{{ itemText }}</div>
    <div class="task-info">
      <span class="task-date">14 June 2022</span>
      <div class="bookmark">
        <span class="bookmark-count"></span>
        <span class="bookmark-icon"></span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    itemText: String,
    taskState: String,
  },
  data() {
    return {
      statusDisplay: false,
    };
  },
  computed: {
    state() {
      let stt = this.taskState;
      return stt;
    },
  },
  methods: {
    setStatus(val) {
      this.$emit("setTaskStatus", val);
      this.statusDisplay = false;
    },
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Devanagari:wght@400;500&display=swap");
.tasks {
  width: 100%;
  height: auto;
  background-color: #f2f2f2;
  border-radius: 5px;
  box-shadow: 0px 0px 2px rgba(118, 96, 126, 0.45);
  padding: 1rem;
  margin-bottom: 1rem;
  .task-status {
    width: 100%;
    height: 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;

    .status {
      color: white;
      height: 14px;
      font-size: 11px;
      text-transform: uppercase;
      font-weight: 500;
      padding: 7px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 3px;
    }
    .set-status-icon {
      cursor: pointer;
      display: flex;
      position: relative;
      .set-status {
        width: 150px;
        height: auto;
        display: flex;
        flex-direction: column;
        position: absolute;
        top: 0;
        right: 20px;
        background-color: #f2f2f2;
        box-shadow: 0px 0px 5px rgba(118, 96, 126, 0.45);
        border-radius: 5px;
        padding: 0 0.3rem;
        .status-item {
          display: flex;
          align-items: center;
          padding: 7px;
          .status-circle {
            height: 14px;
            width: 14px;
            border-radius: 7px;
            display: flex;
            margin-right: 0.5rem;
          }
        }
      }
      svg {
        &:hover {
          path {
            fill: #333333;
          }
        }
      }
    }
  }
  .task-content {
    width: 100%;
    height: auto;
    color: #000;
    font-weight: 400;
    font-size: 16px;
    min-height: 3rem;
    margin: 0.5rem 0;
    font-family: "IBM Plex Sans Devanagari", sans-serif;
    overflow: hidden;
  }
  .task-info {
    .task-date {
      font-size: 12px;
      color: #828282;
      font-weight: 400;
    }
  }

  .active {
    background-color: #556783;
  }
  .completed {
    background-color: #27ae60;
  }
  .pending {
    background-color: #d1b627;
  }
  .onhold {
    background-color: #bebebe;
  }
  .cancelled {
    background-color: #eb5757;
  }
  .confirmed {
    background-color: #9b73aa;
  }
}
</style>
