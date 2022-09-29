<template>
  <section class="hero">
    <div class="heroText">
      <h2><span>Hi there 👋, I'm</span></h2>
      <h1 class="chars">
        <span id="firstName" class="name">
          <span
            class="char"
            v-for="(char, index) in chars"
            :key="char.id"
            :data-index="index"
            >{{ char.text }}</span
          >
        </span>
        <span id="lastName" class="name">
          <span
            class="char"
            v-for="(char, index) in chars2"
            :key="char.id"
            :data-index="index"
            >{{ char.text }}</span
          >
        </span>
      </h1>
      <hr :style="{ backgroundColor: darkBlue, borderColor: darkBlue }" />
      <p>
        <span
          >I'm a creative Fullstack Developer who loves to create elegant and
          functional user interfaces and web apps</span
        >
      </p>
      <div class="buttons">
        <div class="buttoes">
          <Button
            @click="scrollToElement('.work')"
            buttonText="See my work"
            :style="{
              backgroundColor: darkBlue,
              color: whiteBlue,
              borderColor: normalBlue,
            }"
          />
          <Button
            @click="scrollToElement('.contacts')"
            class="lastButton"
            buttonText="Contact me"
            :style="{
              backgroundColor: whiteBlue,
              color: darkBlue,
              borderColor: darkBlue,
            }"
          />
        </div>
      </div>
    </div>
    <div class="imgContainer">
      <img class="tiagoImg" src="@/assets/tiago.png" alt="" />
    </div>
  </section>
</template>

<script>
import Button from "../components/Button.vue";
export default {
  name: "Hero",
  props: {
    darkBlue: String,
    whiteBlue: String,
    normalBlue: String,
  },
  setup() {
    const chars = [
      { id: 0, text: "T" },
      { id: 1, text: "i" },
      { id: 2, text: "a" },
      { id: 3, text: "g" },
      { id: 4, text: "o" },
    ];
    const chars2 = [
      { id: 5, text: "C" },
      { id: 6, text: "o" },
      { id: 7, text: "s" },
      { id: 8, text: "t" },
      { id: 9, text: "a" },
    ];

    return { chars, chars2 };
  },
  components: {
    Button,
  },
  methods: {
    scrollToElement(destination) {
      const element = document.querySelector(destination);
      if (element) {
        element.scrollIntoView({ behavior: "smooth" });
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.pageContent {
  $whiteBlue: #e7ecef;
  $darkBlue: #274c77;
  $normalBlue: #6aa7cf;
  $lightBlue: #a3cef1;
  $editorBlue: #21313c;
  $gostoDesteAzul: #aedbf7;

  $easing: cubic-bezier(0.39, 1.61, 0.89, 1.22);
  $fastEasing: cubic-bezier(0.075, 0.82, 0.165, 1);
  $delay: 0.5s;
  $h1Size: 70px;

  .hero {
    display: flex;
    justify-content: space-between;
    align-items: center;
    overflow: hidden;
    height: 100vh;
    border-bottom: 2px solid $darkBlue;
    padding-top: 25px;
    padding-bottom: 0;
    padding-right: 0;

    .imgContainer {
      overflow: hidden;
      position: relative;
      width: 45%;
      height: 100vh;
      padding-top: -100px;

      .tiagoImg {
        position: absolute;
        display: block;
        width: 100%;
        right: 0;
        bottom: 0;
        z-index: 1;
        transform: translateY(-100%);
        animation: fadeIn 1s forwards;
      }
    }

    .heroText {
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: flex-start;
      z-index: 2;

      h2 {
        font-size: 20px;
        padding-left: 20px;
        margin-bottom: -25px;
        overflow: hidden;

        span {
          display: block;
          transform: translate3d(0, -400px, 0);
          animation: showTopText 1s 0.3s forwards;
        }
      }

      h1 {
        display: flex;
        font-size: 120px;
        padding-left: 20px;
        overflow: hidden;

        .name {
          display: block;
          transform: translate3d(0, -400px, 0);
          animation: showTopText 1s 0.3s forwards;
        }

        #firstName {
          margin-right: 20px;
        }

        .char {
          display: inline-block;
          transition: all 0.5s $fastEasing;

          &:hover {
            color: $normalBlue;
            cursor: default;
            opacity: 1;
            transform: rotate(-5deg) scale(1.1, 1.1) translateX(-5px)
              translateY(-5px) !important;
          }

          &:nth-child(6) {
            margin-left: 25px;
          }
        }
      }

      hr {
        width: 96%;
        background-color: $darkBlue;
        border: 1px solid $darkBlue;
        margin-left: 20px;
        margin-bottom: 20px;
      }

      p {
        width: 500px;
        font-size: 20px;
        padding-left: 20px;
        overflow: hidden;

        span {
          display: block;
          transform: translate3d(0, 100%, 0);
          animation: showBottomText 1s 0.6s 1 normal forwards;
        }
      }

      .buttons {
        padding-left: 20px;
        display: flex;
        overflow: hidden;

        .buttoes {
          width: 100%;
          height: 100%;
          animation: showBottomText 1s 0.6s 1 normal forwards;
          padding-right: 1.5rem;
          padding-top: 2rem;
          padding-bottom: 2rem;
          transform: translateY(-400%);
        }
      }
    }
  }

  @media (max-width: 1450px) {
    .hero .heroText h1 {
      flex-direction: column;
      padding-right: 0;

      #firstName {
        margin-bottom: -50px;
      }
    }

    .hero .imgContainer {
      width: 55%;
    }
  }

  @media (max-width: 1150px) {
    .hero {
      flex-direction: column;
      padding-right: 30px;
      padding-top: 0px;
      margin-bottom: 50px;
      border-bottom: none;

      .heroText {
        width: 100%;

        h1 {
          flex-direction: row;
        }
      }

      .imgContainer {
        position: absolute;
        right: 0;
        bottom: 0;
        width: 70%;
      }
    }
  }

  @media (max-width: 900px) {
    .hero {
      flex-direction: column;
      padding-right: 60px;
      padding-top: 100px;

      .heroText {
        width: 100%;

        h1 {
          flex-direction: column;
        }
      }

      .imgContainer {
        display: none;
      }
    }
  }

  @media (max-width: 600px) {
    .hero {
      flex-direction: column;
      padding-right: 20px;
      padding-left: 20px;
      padding-top: 100px;

      .heroText {
        width: 100%;

        h1 {
          flex-direction: column;
          font-size: 100px;

          #firstName {
            margin-bottom: -30px;
          }
        }

        p {
          width: 100%;
        }

        hr {
          width: 90%;
        }
      }

      .imgContainer {
        display: none;
      }
    }
  }

  @media (max-width: 376px) {
    .hero {
      flex-direction: column;
      padding-right: 20px;
      padding-left: 20px;
      padding-top: 100px;

      .heroText {
        width: 100%;

        h2 {
          padding-left: 0px;
        }

        h1 {
          flex-direction: column;
          font-size: 70px;
          margin-top: 10px;
          padding-left: 0;

          #firstName {
            margin-bottom: -30px;
          }
        }

        p {
          font-size: 16px;
          padding-left: 10px;
        }

        hr {
          margin-left: 10px;
        }

        .buttons {
          padding-left: 10px;
        }
      }
    }
  }
}
</style>
