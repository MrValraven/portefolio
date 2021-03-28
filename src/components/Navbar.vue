<template>

  <header class="header">
    <nav id="nav">
      <div class="logo">
              <router-link class="logoName" to="/">
                  <img src="../assets/logo.png" alt="">
              </router-link>
          </div>
      <ul>
        <li><router-link class="navLinks" to="/">.home<span>()</span></router-link></li>
        <li><router-link class="navLinks" :to="{ name: 'Home' }">.about<span>()</span></router-link></li>
        <li><router-link class="navLinks" :to="{ name: 'Home' }">.work<span>()</span></router-link></li>
        <li><router-link class="navLinks" :to="{ name: 'Home' }">.contacts<span>()</span></router-link></li>
        <li><a  href="https://github.com/MrValraven" target="_blank"><i id="github" class="fab fa-github"></i></a></li>
        <li><a  href="https://www.linkedin.com/in/tiago-costa-b141121b1/" target="_blank"><i id="linkedin" class="fab fa-linkedin"></i></a></li>
      </ul>
	  </nav>
  </header>
    
  
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'Navbar',
});
</script>

<style lang="scss">

@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');

.header {
  position: fixed;
	z-index: 10;
	width: 100%;
	opacity: 1;
	color: #fff;
	padding: 20px 100px 0;
  background: black;
  #nav {
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
        left: 40px;
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
          color: #f7f7f7;
          font-family: 'Roboto', sans-serif;

          &.router-link-exact-active {
            border-bottom: 1px solid black;
          }

          i {
            font-size: 30px;
            transition: all 0.2s ease-in;
          }

          #linkedin:hover {
             color: #2867B2;
          }

          #github:hover {
            color: #6e5494;
          }

          span {
            margin-left: 2px;
            letter-spacing: 5px;
          }
        }  
      }
    }
  }
}
</style>