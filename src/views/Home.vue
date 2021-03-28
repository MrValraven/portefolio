<template>
    <ScrollToTopButton v-if="!isAtTop"  @click="scrollToElement('body')"/>
    <NavbarMobile v-if="(mobileMode && isAtTop) || (activatedNavbar && mobileMode)" @click="activatedNavbar = !activatedNavbar" />
    <Navbar v-if="!mobileMode" class="navbar" />
    <div v-if="!activatedNavbar" class="pageContent">
      <section class="hero">
        <div class="image" :style="{ 'background-image': 'url(' + image + ')' }"></div>
        <div class="labels">
          <div class="designer">
            <h1>Designer</h1>
            <p>A UI/UX Designer with a passion to create beautifull and functional user experiences</p>
          </div>
          <div class="developer">
            <h1>&lt;Developer&gt;</h1>
            <p>A Fullstack developer who focuses on writing clean, elegant and efficient code </p>
          </div>
        </div>
      </section>
      <section class="frases">
        <h1>It's important to think outside of the box</h1>
      </section>
      <section class="funthings">
        <div>
          <h1>About me</h1>
        </div>
      </section>
    </div>
  
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Navbar from '../components/Navbar.vue';
import NavbarMobile from '../components/NavbarMobile.vue';
import ScrollToTopButton from '../components/ScrollToTopButton.vue';
export default defineComponent({
  name: 'Home',
  data() {
    return {
      activatedNavbar: false,
      isAtTop: true,
      mobileMode: false,
      image: 'https://i.pinimg.com/originals/e3/66/87/e366871039caf5afd17b0bcfecb453cb.jpg',
    }
  },
  components: {
    Navbar,
    NavbarMobile,
    ScrollToTopButton,
  },
  created() {
    window.addEventListener('scroll', this.handleScroll);
    this.handleResize();
    window.addEventListener('resize', this.handleResize);
  },
  unmounted() {
    window.removeEventListener('scroll', this.handleScroll);
    window.removeEventListener('resize', this.handleResize);
  },
   methods: {
    getImgURL(image: String) {
        return require('../assets/' + image);
    },
    scrollToElement(destination: string) {
      const element = document.querySelector(destination);
      if (element) {
        element.scrollIntoView({behavior: 'smooth'});
      }
    },
    handleScroll () {
      window.pageYOffset >= 250 ? this.isAtTop = false : this.isAtTop = true;
    },
    handleResize () {
      this.mobileMode = window.innerWidth <= 1015;
      if(!this.mobileMode) {
        this.activatedNavbar = false;
      }
    },
  },
});
</script>

<style lang="scss" scoped>
.hero {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  .image {
    position: absolute;
    background-position: center;
    background-size: cover;
    height: 100%;
    width: 100%;
    background-position: center;
    background-size: cover;
    z-index: 1;
  }

  .labels {
    width: 100%;
    display: flex;
    justify-content: space-around;
    align-items: center;
    z-index: 3;
    border: 2px solid yellow;

    .designer,
    .developer {
      border: 2px solid red;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      width: 30%;
      color: #2c3e50;

      h1 {
        font-size: 70px;
      }

      p {
        width: 80%;
        font-size: 18px;
      }
    }
  }
}

.funthings {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;

  &:hover > div{
    padding: 100px;
    border-radius: 0;
  }

  div {
    padding: 100px;
    border-radius: 50%;
    border: 2px solid red;
    transition: all 0.5s cubic-bezier(0.075, 0.82, 0.165, 1);
  }
}
</style>