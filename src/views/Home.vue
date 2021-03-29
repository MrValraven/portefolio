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
        <a class="cta" @click="scrollToElement('.work')">find out about my work</a>
      </section>
      <section class="work">
        <h1>My latest work</h1>
        <ul class="projects">
          <li>
            <img src="@/assets/work/seistetos.jpg" alt="">
            <div class="cardtext">
              <h2>Grupo Académico Seistetos</h2>
              <p>A simple website redesign and development, bringing this university group's website up to date with a new and fresh layout.</p>
              <p> Helped the group get more online exposure and improved SEO, while also preserving their history, events, group members that have passed through the group and discography all in a simple and intuitive page</p>
              <h3>TechStack:</h3>
              <p>HTML5, Sass, Vue.js, Vue Router, Typescript</p>
              <div class="links">
                <a href="https://github.com/MrValraven/seistetos">Source code</a>
                <a class="liveWebsite" href="https://www.seistetos.uevora.pt/#/">Live Website</a>
              </div>
            </div>
          </li>
        </ul>
      </section>
      <section class="about">
        <div class="aboutMe">
          <h1>But who is this guy?</h1>
          <div class="card">
            <div class="content">
              <h2>Tiago Costa</h2>
              <p>I'm a college senior majoring Computer Science</p>
              <a href="#">Sabe mais</a>
            </div>
            <img class="image" src="@/assets/me.png" alt="">
          </div>
        </div>
        <div class="toolset">
          <h1>My toolset</h1>
          <ul>
            <li>
              <i class="fab fa-java"></i>
              <i class="fab fa-js-square"></i>
              <i class="fab fa-node"></i>
              <i class="fab fa-sass"></i>
              <i class="fab fa-html5"></i>
              <i class="fab fa-figma"></i>
              <i class="fab fa-git-alt"></i>

            </li>
          </ul>
        </div>
        
      </section>
      <section class="estrutura">
        <h1>Hero</h1>
        <h1>work</h1>
        <h1>Skills</h1>
        <h1>But who's this guy?</h1>
        <h1>Contact me</h1>
      </section>
      <section class="frases">
        <h1>It's important to think outside of the box</h1>
        <h1>show personality</h1>
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
section {
  padding: 25px 100px 100px 100px;
}

.hero {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 0;

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

  .cta {
    opacity: 1;
    position: absolute;
    top: 95%;
    left: 47%;
    z-index: 4;
    color: white;
  }
}

.work {
  display: flex;
  justify-content: center;
  align-items: center;  
  flex-direction: column;

  h1 {
    font-size: 50px;
    margin-bottom: 50px;
  }

  img {
    width: 600px;
    margin-right: 25px;
  }

  .projects li {
    display: flex;
    
  }

  .cardtext {
    
    h2 {
      font-size: 50px;
      margin-bottom: 25px;
    }

    p {
      font-size: 16px;
      margin-bottom: 15px;
    }

    h3 {
      font-size: 20px;
      margin-bottom: 10px;
    }
    
    .links {
      

      a {
        background-color: #2c3e50;
        color: white;
        padding: 10px;
        transition: all 0.2s ease-in;
      }

      .liveWebsite {
        margin-left: 10px;
      }
    }
  }
}

.about {
  position: relative;
  display: flex;

  .card {
    position: relative;
    width: 600px;
    height: 350px;
    margin: 20px 20px 0 0;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    background: linear-gradient(45deg, #1a2f3f, #7094ce);
    transition: 0.5s;

    .content {
      position: relative;
      width: 50%;
      left: 20%;
      padding: 20px 20px 20px 40px;
      opacity: 0;
      visibility: hidden;
      transition: 0.5s;

      h2 {
        color: white;
        text-transform: uppercase;
        font-size: 2.2em;
        line-height: 1em;
      }

      p {
        color: white;
      }

      a {
        color: black;
        background-color: white;
        display: inline-block;
        padding: 10px 20px;
        margin-top: 10px;
        font-weight: 700;
      }
    }

    img {
      position: absolute;
      bottom: 0;
      left: 50%;
      transform: translateX(-50%);
      height: 400px;
      transition: all 0.3s ease-in;
    }

    &:hover .content {
      left: 0%;
      opacity: 1;
      visibility: visible;
    }

    &:hover img {
      left: 73%;
      height: 500px;

    }
  }

  .toolset {

    li {
      margin-top: 30px;
    }
    i {
      font-size: 60px;
      margin-right: 30px;
    }
  }
}


@media (max-width: 900px) {

  .card {
    width: auto;
    max-width: 400px;
    justify-content: flex-start;
    align-items: flex-start;
    flex-direction: column;

    &:hover {
      height: 600px;
    }
    
    .content {
      width: 100%;
      top: 0;
      left: 0;
      padding: 40px;
    }

    &:hover > .image {
      left: 0%;
      height: 3350px;
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