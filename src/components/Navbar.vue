<template>

  <header>
    <nav>
      <div class="logo">
              <router-link class="logoName" to="/">
                  <img src="../assets/logo.png" alt="">
              </router-link>
          </div>
      <ul>
        <li @click="this.$emit('home')"><a :style="{color: textColor}">.home</a></li>
        <li @click="this.$emit('work')"><a :style="{color: textColor}">.work</a></li>
        <li @click="this.$emit('about')"><a :style="{color: textColor}">.about</a></li>
        <li @click="this.$emit('contacts')"><a :style="{color: textColor}">.contacts</a></li>
        <li><a :style="{color: textColor}">.curriculumVitae</a></li>
        <li><a :style="{color: textColor}"  href="https://github.com/MrValraven" target="_blank"><i id="github" class="fab fa-github"></i></a></li>
        <li><a :style="{color: textColor}"  href="https://www.linkedin.com/in/tiago-costa-b141121b1/" target="_blank"><i id="linkedin" class="fab fa-linkedin"></i></a></li>
        <li class="sun" @click="this.$emit('toggleTheme') " v-if="!isDarkMode"><a :style="{color: textColor}"><i class="fas fa-sun"></i></a></li>
        <li class="moon" @click="this.$emit('toggleTheme') " v-else><a :style="{color: textColor}"><i class="fas fa-moon"></i></a></li>
      </ul>
	  </nav>
  </header>
    
  
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'Navbar',
  props: {
    isDarkMode: Boolean,
    textColor: String,
  },
  emits: ['home','work','about','contacts', 'toggleTheme'],
});
</script>

<style lang="scss">

@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');

$darkBlue: #274C77;

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
      img {
        width: 50px;
        position: absolute;
        top: 15px;
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
  .header #nav .logo img {
    left: 70px;
  }
}
</style>