<template>
  <div
    class="sideproject-container"
    :style="{
      border: `1px solid ${styles.backgroundColor}`,
    }"
  >
    <div class="text-container">
      <h2>{{ title }}</h2>
      <p>{{ description }}</p>
    </div>
    <div class="button-container">
      <button
        v-if="websiteURL"
        class="website"
        :style="{
          backgroundColor: styles.backgroundColor,
          border: `1px solid ${styles.border}`,
        }"
      >
        <a
          :href="websiteURL"
          target="_blank"
          rel="noreferrer"
          :style="{ color: styles.color }"
          >Live Website</a
        >
      </button>
      <a
        :href="codeURL"
        class="code"
        target="_blank"
        rel="noreferrer"
        :style="{
          border: `1px solid ${styles.backgroundColor}`,
        }"
        ><i
          class="fas fa-code"
          :style="{
            color: styles.backgroundColor,
          }"
        ></i
      ></a>
    </div>
  </div>
</template>

<script>
import Button from "@/components/Button.vue";
export default {
  props: {
    title: String,
    description: String,
    websiteURL: String,
    codeURL: String,
    styles: Object,
  },
  components: {
    Button,
  },
};
</script>

<style lang="scss" scoped>
.sideproject-container {
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  padding: 20px 30px;
  min-width: 23vw;
  max-width: 30vw;
  margin-top: 20px;
  margin-right: 20px;
  border-radius: 25px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 20px 100px -20px,
    rgba(0, 0, 0, 0.3) 0px 30px 60px -30px,
    rgba(10, 37, 64, 0.35) 0px -2px 6px 0px inset;

  p {
    margin: 10px 0px;
  }

  .button-container {
    display: flex;
    justify-content: flex-end;

    .website {
      font-size: 16px;
      padding: 10px;
      border-radius: 10px;
      outline: none;
      border: none;
      transition: all 0.5s cubic-bezier(0.075, 0.82, 0.165, 1);

      &:hover {
        cursor: pointer;
        filter: brightness(0.9);
      }

      a {
        opacity: 1;
      }
    }

    .code {
      font-size: 16px;
      padding: 8px 10px;
      border-radius: 10px;
      opacity: 1;
      margin-left: 10px;
      transition: all 0.5s cubic-bezier(0.075, 0.82, 0.165, 1);

      &:hover {
        cursor: pointer;
        filter: brightness(0.7);
      }
    }
  }
}

@media (max-width: 900px) {
  .sideproject-container {
    min-width: 46%;
    max-width: 46%;
    width: 46%;
  }
}
@media (max-width: 600px) {
  .sideproject-container {
    min-width: 100%;
    max-width: 100%;
    width: 100%;
  }
}
</style>
