<template>
    <ScrollToTopButton v-if="!isAtTop"  @click="scrollToElement('body')"/>
    <NavbarMobile v-if="(mobileMode && isAtTop) || (activatedNavbar && mobileMode)" @click="activatedNavbar = !activatedNavbar" />
    <Navbar v-if="!mobileMode" class="navbar" />
    <div v-if="!activatedNavbar" class="pageContent">
      <section class="hero">
        <div class="heroText">
          <h2><span>Hi there 👋, I'm</span></h2>
          <h1
          class="chars" 
          >
            <span id="name"><span class="char" v-for="(char, index) in chars" :key="char.id" :data-index="index">{{ char.text }}</span></span>
          </h1>
          <hr>
          <p><span>I'm a creative Fullstack Developer who loves to create elegant and functional user interfaces and web apps</span></p>
          <div class="buttons">
            <div class="buttoes">
              <Button @click="scrollToElement('.work')" buttonText="See my work"/>
              <Button class="lastButton" buttonText="Contact me" />
            </div>
          </div>
        </div>
        <div class="imgContainer">
          <img class="tiagoImg" src="@/assets/tiago.png" alt="">
        </div>
      </section>
      <section class="work">
        <ul class="projects">
          <li>
            <div class="cardtext">
              <h2><span>Grupo Académico Seistetos</span></h2>
              <h3><span>Front-end development and UX/UI Website Design</span></h3>
              <p>
                <span class="line1" >
                  <span id="span1" >A simple website redesign and </span>
                </span>
                <span class="line1" >
                  <span id="span2">development, bringing this</span>
                </span>
                <span class="line1" >
                  <span id="span3">university group's website up to</span>
                </span>
                <span class="line1">
                  <span id="span4">date with a new and fresh layout.</span>
                </span>
              </p>
             <!--  <p> Helped the group get more online exposure and improved SEO, while also preserving their history, events, group members that have passed through the group and discography all in a simple and intuitive page</p> -->
              <h4><span>TechStack:</span></h4>
              <p class="tech"><span>HTML5, Sass, Vue.js, Vue Router, Typescript</span></p>
              <div class="links">
                <div class="link">
                  <Button buttonText="Live Website" link="https://www.seistetos.uevora.pt/#/" />
                  <Button class="lastButton" buttonText="Source Code" link="https://github.com/MrValraven/seistetos" />
                </div>
              </div>
            </div>
            <img class="mainImage" src="@/assets/work/seistetos/seistetos.jpg" alt="">
            <img class id="hoverImg" src="@/assets/work/seistetos/seistetosLogo.png" alt="">
          </li>
          <li>
            <div class="cardtext">
              <h2>Expo Estudante</h2>
              <h3>Front-end development</h3>
              <p>A modern approach to the upcoming technology and student oriented event in Évora, Portugal.</p>

              <h4>TechStack:</h4>
              <p class="tech">HTML5, Sass, Vue.js, Vue Router, Typescript</p>
              <div class="links">
                <Button buttonText="Live Website" link="https://expoestudante.aaue.pt/#/" />
              </div>
            </div>
            <img class="mainImage" src="@/assets/work/expoestudante/expoestudante.jpg" alt="">
          </li>
        </ul>
      </section>
      <section class="about" v-if="finished">
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
      <section class="estrutura" v-if="finished">
        <h1>Hero</h1>
        <h1>work</h1>
        <h1>Skills</h1>
        <h1>But who's this guy?</h1>
        <h1>Contact me</h1>
      </section>
      <section class="frases" v-if="finished">
        <h1>It's important to think outside of the box</h1>
        <h1>show personality</h1>
      </section>
      <section class="funthings" v-if="finished">
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
import Button from '../components/Button.vue';
import gsap from 'gsap';

export default defineComponent({
  name: 'Home',
  setup() {
        const chars = [
            {id: 0, text: "T"},
            {id: 1, text: "i"},
            {id: 2, text: "a"},
            {id: 3, text: "g"},
            {id: 4, text: "o"},
            {id: 5, text: "C"},
            {id: 6, text: "o"},
            {id: 7, text: "s"},
            {id: 8, text: "t"},
            {id: 9, text: "a"},
        ]
        const beforeEnter: any = (el: any) => {
            el.style.opacity = 0;
            el.style.transform = 'rotate(-5deg) scale(1.1, 1.1) translateX(-10px) translateY(-10px)';
        }
        const enter: any = (el: any, done: any) => {
            gsap.to(el, {
                opacity: 1,
                x: 0,
                y: 0,
                rotation: 0,
                duration: 1,
                scale: 1,
                ease: 'power3',
                onComplete: done,
                delay: el.dataset.index * 0.1,
            });
        }
        return { chars, beforeEnter, enter }
    },
  data() {
    return {
      activatedNavbar: false,
      isAtTop: true,
      mobileMode: false,
      finished: false,
      image: 'https://i.pinimg.com/originals/e3/66/87/e366871039caf5afd17b0bcfecb453cb.jpg',
    }
  },
  components: {
    Navbar,
    NavbarMobile,
    ScrollToTopButton,
    Button,
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

@import url('https://fonts.googleapis.com/css?family=Roboto:700');
@keyframes showTopText {
  0% { 
    transform: translate3d(0, 100%, 0);
   }

  100% { 
    transform: translate3d(0, 0, 0); 
  }
}
@keyframes showBottomText {
  0% { transform: translate3d(0, -300%, 0); }
  100% { transform: translate3d(0, 0, 0); }
}

@keyframes fadeIn {
  0% {
    transform: translateY(100%);
  }

  100% {
    transform: translateY(0%);
  }
}

$whiteBlue: #E7ECEF;
$darkBlue: #274C77;
$normalBlue: #6aa7cf;
$lightBlue: #A3CEF1;
$easing: cubic-bezier(0.39, 1.61, 0.89, 1.22);
$fastEasing: cubic-bezier(0.075, 0.82, 0.165, 1);

section {
  padding: 100px;
}

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
      animation: fadeIn 1s  forwards;
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
      font-size: 120px;
      padding-left: 20px;
      overflow: hidden;

      #name {
        display: block;
        transform: translate3d(0, -400px, 0);
        animation: showTopText 1s 0.3s forwards;
      }

      .char {
        display: inline-block;
        transition: all 0.5s $fastEasing;

        &:hover {
          color: $normalBlue;
          cursor: default;
          opacity: 1;
          transform: rotate(-5deg) scale(1.1, 1.1) translateX(-5px) translateY(-5px) !important;
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


.work {
  display: flex;
  justify-content: center;
  align-items: flex-start;  
  flex-direction: column;
  position: relative;

  .mainImage {
    min-width: 55%;
    border: 5px solid black;
    border-radius: 16px;
    margin-right: 25px;
    box-shadow: 0px 5px 25px 0px rgba($color: #000000, $alpha: 0.3);
  }

  #hoverImg {
    position: absolute;
    height: 400px;
    left: 38%;
    bottom: 55%;
  }

  .projects {
    width: 100%;
    height: 100%;

    li {
      display: flex;
      min-height: 70vh;
      border-bottom: 2px solid #cecccc9a;
      padding-bottom: 10vh;
      margin-bottom: 10vh;
      
    }
  }
  
  

  .cardtext {
    margin-left: 5px;

    
    h2 {
      display: inline-flex;
      font-size: 70px;
      font-weight: 500;
      margin-left: -5px;
      line-height: 60px;
      overflow: hidden;

      span {
        display: block;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 0.3s forwards;
      }
    }

     h3 {
      font-size: 16px;
      font-weight: 300;
      opacity: 0.8;
      margin-top: 20px;
      margin-bottom: 30px;
      overflow: hidden;

       span {
        display: block;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 0.4s forwards;
      }
    }

    p {
      width: 70%;
      font-size: 30px;
      margin-bottom: 30px;
      overflow: hidden;

      .line1 {
        display: inline-flex;
        transform: translate3d(0, 0%, 0);
        overflow: hidden;
      }

      #span1 {
        display: block;
        animation-delay: 0.7s !important;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 0.7s forwards;

      }
      #span2 {
        display: block;
        animation-delay: 0.8s !important;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 0.8s forwards;
        line-height: 1.4em;

      }
      #span3 {
        display: block;
        animation-delay: 0.9s !important;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 0.8s forwards;
        line-height: 1.4em;

      }
      #span4 {
        display: block;
        animation-delay: 1s !important;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 1.0s forwards;
        line-height: 1.4em;

      }
    }

    h4 {
      font-size: 25px;
      overflow: hidden;

       span {
        display: block;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 1.1s forwards;
      }
    }

    .tech {
      font-size: 16px;
      opacity: 0.8;
      overflow: hidden;

       span {
        display: block;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 1.2s forwards;
      }
    }

    .links {
      margin-top: 30px;
      padding: 20px 0 20px 0;
      overflow: hidden;

      .link {
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 1.3s forwards;
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