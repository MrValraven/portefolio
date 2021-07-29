<template>

  <header>
    <nav>
      <div class="logo">
              <router-link class="logoName" to="/">
                  <img src="../assets/logo.png" alt="">
              </router-link>
          </div>
      <ul>
        <li @click="this.$emit('home')"><a>.home</a></li>
        <li @click="this.$emit('work')"><a>.work</a></li>
        <li @click="this.$emit('about')"><a>.about</a></li>
        <li @click="this.$emit('contacts')"><a>.contacts</a></li>
        <li><a  href="https://github.com/MrValraven" target="_blank"><i id="github" class="fab fa-github"></i></a></li>
        <li><a  href="https://www.linkedin.com/in/tiago-costa-b141121b1/" target="_blank"><i id="linkedin" class="fab fa-linkedin"></i></a></li>
        <li v-if="!isDarkMode"><a><i class="fas fa-sun"></i></a></li>
        <li v-else><a><i class="fas fa-moon"></i></a></li>
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
  },
  emits: ['home','work','about','contacts'],
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
    }
  }
}

@media (max-width: 1680px) {
  .header #nav .logo img {
    left: 70px;
  }
}
</style>