<template>
  <header>
    <nav>
      <div class="logo">
        <router-link class="logoName" to="/">
          <svg
            v-if="!isDarkMode"
            id="Camada_1"
            data-name="Camada 1"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 1366 768"
          >
            <path
              d="M1215.27,498.15c-23.08-56.88-69.26-154.13-92.34-189-22.61-34.14-45.22,3.85-46.15,5.45a.41.41,0,0,1-.07.11c-1.71,2.49-55.7,81.14-76.15,110-20.77,29.36-23.08,29.36-73.87,22s-168.54,0-203.17,7.34S682,448.61,675,426.59s-25.4-62.39-51.95-102.49-49.63-7.6-49.63-7.6-50.8,73.39-103.9,196.33C419.32,629.14,398.81,704.92,398.81,733h879.62C1277.34,601.68,1237.83,553.72,1215.27,498.15Zm-651.06,5.9c-10.31-.54-21-8.57-14.68-26.78,11.6-33.29,22.52-62.29,40.7-62.09,13.14.14,36.87,46.12,45.92,64.54A14.77,14.77,0,0,1,624.22,501C607.6,502.44,581.38,504.94,564.21,504.05ZM728.69,682.46a36.48,36.48,0,0,1-12.25,18.34h0a2.63,2.63,0,0,1-4.22-1.55c-1.93-9.44-9.16-30.59-35.2-28.41-23.18,1.94-26.94,19.21-27.07,29.6a2.62,2.62,0,0,1-4.66,1.63c-14.35-18-48.47-69.73,23.72-79.23C740.42,613.45,735.25,659.75,728.69,682.46Zm313,19.61a2.62,2.62,0,0,1-4.67-1.63c-.13-10.39-3.89-27.66-27.07-29.6-26-2.18-33.27,19-35.19,28.41a2.64,2.64,0,0,1-4.23,1.55h0a36.48,36.48,0,0,1-12.25-18.34c-6.56-22.71-11.73-69,59.68-59.62C1090.14,632.34,1056,684.06,1041.67,702.07ZM1126,503.24c-17.17.89-43.38-1.6-60-3.07a14.78,14.78,0,0,1-11.93-21.25c9-18.43,32.78-64.41,45.93-64.55,18.17-.19,29.09,28.81,40.69,62.1C1147,494.68,1136.31,502.71,1126,503.24Z"
            />
            <path
              d="M561.18,199.6c43.4-17.84,15.57-84.41-77-136.75S302.6,34.61,243.54,72.29s-105,107.63-134.2,175.83-28.2,172.47-1.85,290.73C123.57,611,151.2,675.31,181.26,735.31H327.67C271.36,648.05,247.47,600,223.13,500.8c-9.47-38.59-25-88.23,3.52-220.62,16-74.32,78.65-124.69,118.07-133.34,37.39-8.21,81.39-10.74,111.41,13.9C488.59,187.4,525.25,214.37,561.18,199.6Z"
            />
          </svg>
          <svg
            v-else
            id="Camada_1"
            data-name="Camada 1"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 1366 768"
          >
            <path
              class="cls-1"
              d="M1215.27,498.15c-23.08-56.88-69.26-154.13-92.34-189-22.61-34.14-45.22,3.85-46.15,5.45a.41.41,0,0,1-.07.11c-1.71,2.49-55.7,81.14-76.15,110-20.77,29.36-23.08,29.36-73.87,22s-168.54,0-203.17,7.34S682,448.61,675,426.59s-25.4-62.39-51.95-102.49-49.63-7.6-49.63-7.6-50.8,73.39-103.9,196.33C419.32,629.14,398.81,704.92,398.81,733h879.62C1277.34,601.68,1237.83,553.73,1215.27,498.15Z"
            />
            <path
              d="M1066,500.17a14.78,14.78,0,0,1-11.93-21.25c9-18.43,32.78-64.41,45.93-64.55,18.17-.19,29.09,28.81,40.69,62.1,6.34,18.21-4.37,26.24-14.68,26.77C1108.83,504.13,1082.62,501.64,1066,500.17Z"
            />
            <path
              d="M624.22,501a14.77,14.77,0,0,0,11.93-21.25c-9-18.42-32.78-64.4-45.92-64.54-18.18-.2-29.1,28.8-40.7,62.09-6.34,18.21,4.37,26.24,14.68,26.78C581.38,504.94,607.6,502.44,624.22,501Z"
            />
            <path
              class="cls-1"
              d="M107.49,538.85c-26.35-118.26-27.38-222.53,1.85-290.73S184.48,110,243.54,72.29,391.65,10.51,484.2,62.85s120.38,118.91,77,136.75c-35.93,14.77-72.59-12.2-105-38.86-30-24.64-74-22.11-111.41-13.9-39.42,8.65-102.05,59-118.07,133.34-28.53,132.39-13,182-3.52,220.62C247.47,600,271.36,648.05,327.67,735.31H181.26C151.2,675.31,123.57,611,107.49,538.85Z"
            />
            <path
              d="M669,622.84c71.41-9.39,66.24,36.91,59.68,59.62a36.48,36.48,0,0,1-12.25,18.34h0a2.63,2.63,0,0,1-4.22-1.55c-1.93-9.44-9.16-30.59-35.2-28.41-23.18,1.94-26.94,19.21-27.07,29.6a2.62,2.62,0,0,1-4.66,1.63C630.94,684.06,596.82,632.34,669,622.84Z"
            />
            <path
              d="M1041.67,702.07a2.62,2.62,0,0,1-4.67-1.63c-.13-10.39-3.89-27.66-27.07-29.6-26-2.18-33.27,19-35.19,28.41a2.64,2.64,0,0,1-4.23,1.55h0a36.48,36.48,0,0,1-12.25-18.34c-6.56-22.71-11.73-69,59.68-59.62C1090.13,632.34,1056,684.06,1041.67,702.07Z"
            />
          </svg>
        </router-link>
      </div>
      <ul>
        <li @click="this.$emit('home')">
          <a :style="{ color: textColor }">.home()</a>
        </li>
        <li @click="this.$emit('work')">
          <a :style="{ color: textColor }">.work()</a>
        </li>
        <li @click="this.$emit('about')">
          <a :style="{ color: textColor }">.about()</a>
        </li>
        <li @click="this.$emit('contacts')">
          <a :style="{ color: textColor }">.contacts()</a>
        </li>
        <li>
          <a
            :style="{ color: textColor }"
            :href="getPdfURL('cv_tiagoCosta.pdf')"
            >.curriculumVitae()</a
          >
        </li>
        <li>
          <a
            :style="{ color: textColor }"
            href="https://github.com/MrValraven"
            target="_blank"
            ><i id="github" class="fab fa-github"></i
          ></a>
        </li>
        <li>
          <a
            :style="{ color: textColor }"
            href="https://www.linkedin.com/in/tiago-costa-b141121b1/"
            target="_blank"
            ><i id="linkedin" class="fab fa-linkedin"></i
          ></a>
        </li>
        <li class="sun" @click="this.$emit('toggleTheme')" v-if="!isDarkMode">
          <a :style="{ color: textColor }"><i class="fas fa-sun"></i></a>
        </li>
        <li class="moon" @click="this.$emit('toggleTheme')" v-else>
          <a :style="{ color: textColor }"><i class="fas fa-moon"></i></a>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "Navbar",
  props: {
    isDarkMode: Boolean,
    textColor: String,
  },
  emits: ["home", "work", "about", "contacts", "toggleTheme"],
  methods: {
    getImgURL(image: string) {
      return require("../assets/" + image);
    },
    getPdfURL(fileName: string) {
      return require("@/assets/" + fileName).default;
    },
  },
});
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap");

$darkBlue: #274c77;

header {
  position: absolute;
  z-index: 10;
  width: 100%;
  opacity: 1;
  color: #fff;
  padding: 20px 100px 0;

  nav {
    display: flex;
    justify-content: space-between;
    .logo {
      a {
        opacity: 1;
      }
      svg {
        width: 50px;
        position: absolute;
        top: 30px;
        left: 120px;
      }
    }
    ul {
      display: flex;
      justify-content: space-around;
      li {
        padding: 10px;
        font-size: 22px;
        a {
          font-weight: bold;
          font-family: monospace;
          color: $darkBlue;
          transition: all 0.5s cubic-bezier(0.075, 0.82, 0.165, 1) !important;

          &:hover {
            opacity: 1;
          }

          i {
            font-size: 30px;
            transition: all 0.2s cubic-bezier(0.075, 0.82, 0.165, 1);
          }

          #linkedin:hover {
            transform: translateY(-5px);
          }

          #github:hover {
            transform: translateY(-5px);
          }
        }
      }

      .sun,
      .moon {
        transform: translateY(-300%);
        opacity: 0;
        animation: dropDown 0.5s cubic-bezier(0.075, 0.82, 0.165, 1) forwards;
      }

      @keyframes dropDown {
        0% {
          transform: translateY(-300%);
          opacity: 0;
        }
        100% {
          transform: translateY(0%);
          opacity: 1;
        }
      }
    }
  }
}

@media (max-width: 1680px) {
  header nav .logo svg {
    left: 80px;
  }
}

.cls-1 {
  fill: #fff;
}
</style>
