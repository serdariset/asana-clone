<template>
  <div class="section-container">
    <div class="section-header">
      <div class="section-name">
        <div class="input-group">
          <input
            type="text"
            placeholder="Text"
            v-model="sectionName"
            class="section-input"
            :ref="'input'"
            :class="inputDisplay ? 'active' : ''"
            @keyup.enter="inputDisplay = false"
          />
          <label
            for="section-name"
            class="section-label"
            @click="inputDisplay = true"
            v-show="!inputDisplay"
          >
            {{ sectionName }}
          </label>
        </div>
      </div>
      <div class="section-options">
        <span class="add-item">
          <svg
            width="16"
            height="16"
            viewBox="0 0 100 100"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <g clip-path="url(#clip0_1_25)">
              <path
                d="M50 93.75C38.3968 93.75 27.2688 89.1406 19.0641 80.9359C10.8594 72.7312 6.25 61.6032 6.25 50C6.25 38.3968 10.8594 27.2688 19.0641 19.0641C27.2688 10.8594 38.3968 6.25 50 6.25C61.6032 6.25 72.7312 10.8594 80.9359 19.0641C89.1406 27.2688 93.75 38.3968 93.75 50C93.75 61.6032 89.1406 72.7312 80.9359 80.9359C72.7312 89.1406 61.6032 93.75 50 93.75ZM50 100C63.2608 100 75.9785 94.7322 85.3553 85.3553C94.7322 75.9785 100 63.2608 100 50C100 36.7392 94.7322 24.0215 85.3553 14.6447C75.9785 5.26784 63.2608 0 50 0C36.7392 0 24.0215 5.26784 14.6447 14.6447C5.26784 24.0215 0 36.7392 0 50C0 63.2608 5.26784 75.9785 14.6447 85.3553C24.0215 94.7322 36.7392 100 50 100Z"
                fill="#333333"
              />
              <path
                d="M50 25C50.8288 25 51.6237 25.3292 52.2097 25.9153C52.7958 26.5013 53.125 27.2962 53.125 28.125V46.875H71.875C72.7038 46.875 73.4987 47.2042 74.0847 47.7903C74.6708 48.3763 75 49.1712 75 50C75 50.8288 74.6708 51.6237 74.0847 52.2097C73.4987 52.7958 72.7038 53.125 71.875 53.125H53.125V71.875C53.125 72.7038 52.7958 73.4987 52.2097 74.0847C51.6237 74.6708 50.8288 75 50 75C49.1712 75 48.3763 74.6708 47.7903 74.0847C47.2042 73.4987 46.875 72.7038 46.875 71.875V53.125H28.125C27.2962 53.125 26.5013 52.7958 25.9153 52.2097C25.3292 51.6237 25 50.8288 25 50C25 49.1712 25.3292 48.3763 25.9153 47.7903C26.5013 47.2042 27.2962 46.875 28.125 46.875H46.875V28.125C46.875 27.2962 47.2042 26.5013 47.7903 25.9153C48.3763 25.3292 49.1712 25 50 25Z"
                fill="#333333"
              />
            </g>
            <defs>
              <clipPath id="clip0_1_25">
                <rect width="100" height="100" fill="white" />
              </clipPath>
            </defs>
          </svg>
        </span>
        <span class="trash-section">
          <svg
            width="16"
            height="16"
            viewBox="0 0 100 100"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M34.375 34.375C35.2038 34.375 35.9987 34.7042 36.5847 35.2903C37.1708 35.8763 37.5 36.6712 37.5 37.5V75C37.5 75.8288 37.1708 76.6237 36.5847 77.2097C35.9987 77.7958 35.2038 78.125 34.375 78.125C33.5462 78.125 32.7513 77.7958 32.1653 77.2097C31.5792 76.6237 31.25 75.8288 31.25 75V37.5C31.25 36.6712 31.5792 35.8763 32.1653 35.2903C32.7513 34.7042 33.5462 34.375 34.375 34.375ZM50 34.375C50.8288 34.375 51.6237 34.7042 52.2097 35.2903C52.7958 35.8763 53.125 36.6712 53.125 37.5V75C53.125 75.8288 52.7958 76.6237 52.2097 77.2097C51.6237 77.7958 50.8288 78.125 50 78.125C49.1712 78.125 48.3763 77.7958 47.7903 77.2097C47.2042 76.6237 46.875 75.8288 46.875 75V37.5C46.875 36.6712 47.2042 35.8763 47.7903 35.2903C48.3763 34.7042 49.1712 34.375 50 34.375ZM68.75 37.5C68.75 36.6712 68.4208 35.8763 67.8347 35.2903C67.2487 34.7042 66.4538 34.375 65.625 34.375C64.7962 34.375 64.0013 34.7042 63.4153 35.2903C62.8292 35.8763 62.5 36.6712 62.5 37.5V75C62.5 75.8288 62.8292 76.6237 63.4153 77.2097C64.0013 77.7958 64.7962 78.125 65.625 78.125C66.4538 78.125 67.2487 77.7958 67.8347 77.2097C68.4208 76.6237 68.75 75.8288 68.75 75V37.5Z"
              fill="#828282"
            />
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M90.625 18.75C90.625 20.4076 89.9665 21.9973 88.7944 23.1694C87.6223 24.3415 86.0326 25 84.375 25H81.25V81.25C81.25 84.5652 79.933 87.7446 77.5888 90.0888C75.2446 92.433 72.0652 93.75 68.75 93.75H31.25C27.9348 93.75 24.7554 92.433 22.4112 90.0888C20.067 87.7446 18.75 84.5652 18.75 81.25V25H15.625C13.9674 25 12.3777 24.3415 11.2056 23.1694C10.0335 21.9973 9.375 20.4076 9.375 18.75V12.5C9.375 10.8424 10.0335 9.25268 11.2056 8.08058C12.3777 6.90848 13.9674 6.25 15.625 6.25H37.5C37.5 4.5924 38.1585 3.00269 39.3306 1.83058C40.5027 0.65848 42.0924 0 43.75 0L56.25 0C57.9076 0 59.4973 0.65848 60.6694 1.83058C61.8415 3.00269 62.5 4.5924 62.5 6.25H84.375C86.0326 6.25 87.6223 6.90848 88.7944 8.08058C89.9665 9.25268 90.625 10.8424 90.625 12.5V18.75ZM25.7375 25L25 25.3687V81.25C25 82.9076 25.6585 84.4973 26.8306 85.6694C28.0027 86.8415 29.5924 87.5 31.25 87.5H68.75C70.4076 87.5 71.9973 86.8415 73.1694 85.6694C74.3415 84.4973 75 82.9076 75 81.25V25.3687L74.2625 25H25.7375ZM15.625 18.75V12.5H84.375V18.75H15.625Z"
              fill="#828282"
            />
          </svg>
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Section",
  props: {
    name: String,
    count: Number,
  },
  data() {
    return {
      sectionName: "",
      inputDisplay: false,
    };
  },
  mounted() {
    if (!this.name) {
      this.sectionName = "New Section";
    } else {
      this.sectionName = this.name;
    }
  },
};
</script>

<style lang="scss">
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
  .section-header {
    display: flex;
    justify-content: space-between;
    width: 100%;
    height: 2rem;
    align-items: center;
    margin-bottom: 1rem;

    .section-name {
      display: flex;
      margin-right: 2rem;
      width: auto;
      min-width: 250px;

      .section-input {
        border: none;
        outline: none;
        display: none;
        font-size: 20px;
        min-width: 250px;
        height: 1.8rem;
        font-weight: 500;
        font-family: "IBM Plex Sans", sans-serif;
      }
      .active {
        border-bottom: 2px solid #03a9f4;
        background-color: rgba($color: #03a9f4, $alpha: 0.1);
        display: flex;
        align-items: flex-start;
      }
      .section-label {
        display: flex;
        cursor: text;
        font-size: 20px;
        width: 100%;
        min-width: 250px;
        font-weight: 500;
      }
    }
    .section-options {
      display: flex;
      height: 2rem;
      align-items: center;
      span {
        cursor: pointer;
        height: 2rem;
        display: flex;
        align-items: center;

        &:nth-child(1) {
          margin-right: 0.5rem;

          &:hover {
            path {
              fill: green;
            }
          }
        }
        &:nth-child(2) {
          &:hover {
            path {
              fill: red;
            }
          }
        }
      }
    }
  }
}
</style>
