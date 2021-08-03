<template>
    <ScrollToTopButton v-if="!isAtTop"  @click="scrollToElement('body')"/>
    <li class="sun darkIcon" @click="toggleDarkMode()" v-if="!isDarkMode && mobileMode"><a :style="{color: darkBlue}"><i class="fas fa-sun"></i></a></li>
    <li class="moon darkIcon" @click="toggleDarkMode()" v-else-if="isDarkMode && mobileMode"><a :style="{color: darkBlue}"><i class="fas fa-moon"></i></a></li>
    <NavbarMobile  v-if="mobileMode" :textColor="darkBlue" :backgroundColor="whiteBlue"/>
    <Navbar v-if="!mobileMode" class="navbar" @toggleTheme="toggleDarkMode()" :textColor="darkBlue" :isDarkMode="isDarkMode" @home="scrollToElement('body')"  @work="scrollToElement('.work')" @about="scrollToElement('.about')"  @contacts="scrollToElement('.contacts')"/>
    <div v-if="!activatedNavbar" class="pageContent" :style="{backgroundColor: whiteBlue, color: darkBlue} ">
      <section class="hero">
        <div class="heroText">
          <h2><span>Hi there 👋, I'm</span></h2>
          <h1
          class="chars" 
          >
            <span id="firstName" class="name">
              <span class="char" v-for="(char, index) in chars" :key="char.id" :data-index="index">{{ char.text }}</span>
            </span> 
            <span id="lastName" class="name">
              <span class="char" v-for="(char, index) in chars2" :key="char.id" :data-index="index">{{ char.text }}</span>
            </span>
          </h1>
          <hr :style="{backgroundColor: darkBlue, borderColor: darkBlue} ">
          <p><span>I'm a creative Fullstack Developer who loves to create elegant and functional user interfaces and web apps</span></p>
          <div class="buttons">
            <div class="buttoes">
              <Button @click="scrollToElement('.work')" buttonText="See my work" :style="{backgroundColor: darkBlue, color: whiteBlue, borderColor: normalBlue}"/>
              <Button @click="scrollToElement('.contacts')" class="lastButton" buttonText="Contact me" :style="{backgroundColor: whiteBlue, color: darkBlue, borderColor: darkBlue}"/>
            </div>
          </div>
        </div>
        <div class="imgContainer">
          <img class="tiagoImg" src="@/assets/tiago.png" alt="">
        </div>
      </section>
      <section class="work">
        <ul class="projects">
          <li class="seistetos">
            <div class="cardtext" :style="{opacity: opacityTeto}">
              <h2><span :class="{animate: isOnTeto}">Grupo Académico Seistetos</span></h2>
              <h3><span :class="{animate: isOnTeto}">Front-end development and UX/UI Website Design</span></h3>
              <p>
                <span :class="{line1: isOnTeto}"  >
                  <span :class="{span1: isOnTeto}" >A simple website redesign and </span>
                </span>
                <span :class="{line1: isOnTeto}"  >
                  <span :class="{span2: isOnTeto}">development, bringing this</span>
                </span>
                <span :class="{line1: isOnTeto}"  >
                  <span :class="{span3: isOnTeto}">university group's website up to</span>
                </span>
                <span :class="{line1: isOnTeto}">
                  <span :class="{span4: isOnTeto}">date with a new and fresh layout.</span>
                </span>
              </p>
             <!--  <p> Helped the group get more online exposure and improved SEO, while also preserving their history, events, group members that have passed through the group and discography all in a simple and intuitive page</p> -->
              <h4><span :class="{animate: isOnTeto}">TechStack:</span></h4>
              <p class="tech"><span :class="{animate: isOnTeto}">HTML5, Sass, Vue.js, Vue Router, Typescript</span></p>
              <div class="links">
                <div :class="{link: isOnTeto}">
                  <Button buttonText="Live Website" link="https://www.seistetos.uevora.pt/#/" :style="{backgroundColor: darkBlue, color: whiteBlue, borderColor: normalBlue}"/>
                  <Button class="lastButton" buttonText="Source Code" link="https://github.com/MrValraven/seistetos" :style="{backgroundColor: whiteBlue, color: darkBlue, borderColor: darkBlue}"/>
                </div>
              </div>
            </div>
            <img class="mainImage" src="@/assets/work/seistetos/seistetos.jpg" alt="">
            <img class id="hoverImg" src="@/assets/work/seistetos/seistetosLogo.png" alt="">
          </li>
          <li class="expoestudante">
            <div class="cardtext" :style="{opacity: opacityExpo}">
              <h2><span :class="{animate: isOnExpo}">Expo Estudante</span></h2>
              <h3><span :class="{animate: isOnExpo}">Front-end development</span></h3>
              <p>
                <span :class="{line1: isOnExpo}">
                  <span :class="{span1: isOnExpo}">A modern approach to the </span>
                </span>
                <span  :class="{line1: isOnExpo}">
                  <span :class="{span2: isOnExpo}"> upcoming technology and </span>
                </span>
                <span :class="{line1: isOnExpo}">
                  <span :class="{span3: isOnExpo}"> student oriented event in </span>
                </span>
                <span :class="{line1: isOnExpo}">
                  <span :class="{span4: isOnExpo}"> Évora, Portugal.</span>
                </span>
              </p>
             <!--  <p> Helped the group get more online exposure and improved SEO, while also preserving their history, events, group members that have passed through the group and discography all in a simple and intuitive page</p> -->
              <h4><span :class="{animate: isOnExpo}">TechStack:</span></h4>
              <p class="tech"><span :class="{animate: isOnExpo}">HTML5, Sass, Vue.js, Vue Router, Typescript</span></p>
              <div class="links">
                <div :class="{link: isOnExpo}">
                  <Button buttonText="Live Website" link="https://expoestudante.aaue.pt/#/" :style="{backgroundColor: darkBlue, color: whiteBlue, borderColor: normalBlue}"/>
                </div>
              </div>
            </div>
            <img class="mainImage" src="@/assets/work/expoestudante/expoestudante.jpg" alt="">
            <img class id="hoverExpo" src="@/assets/work/expoestudante/logo.png" alt="">
          </li>     
        </ul>
      </section>
      <section class="about">
        <div class="aboutMe">
          <div class="card">
            <h1 class="title">Home.vue - portefolio - Visual Studio Code</h1>
            <h1 class="file">
              <span>
                <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 48 48" width="20px" height="20px"><polygon fill="#81c784" points="23.987,17 18.734,8 2.974,8 23.987,44 45,8 29.24,8"/><polygon fill="#455a64" points="29.24,8 23.987,17 18.734,8 11.146,8 23.987,30 36.828,8"/></svg>
                Home.vue 
                <i class="fas fa-times"></i>
                </span>
              </h1>
            <h2>src
              <i class="fas fa-chevron-right"></i> 
              views
              <i class="fas fa-chevron-right"></i> 
              <b>{}</b> "Home.vue" 
              <i class="fas fa-chevron-right"></i> 
              <i class="fas fa-box"></i>
              template
              <i class="fas fa-chevron-right"></i> 
              <i class="fas fa-box"></i>
              div.pageContent
              <i class="fas fa-chevron-right"></i> 
              <i class="fas fa-box"></i>
              div.aboutMe
              <i class="fas fa-chevron-right"></i> 
              <i class="fas fa-box"></i>
              div.card
              </h2>
              <div class="editor">

                <div class="lineNumbers">
                  <p v-for="number in lineNumbers" :key="number">{{ number }}</p>
                </div>
                <div class="code">
                  <p>&nbsp;</p>
                  <p>
                    <span class="code-purple const"></span>
                    <span id="me" class="code-red"></span >
                    <span id="igual1"></span>
                    <span id="chavetas1" class="code-purple"></span>
                  </p>
                  <p>
                    <span id="nome" class="code-red"></span>
                    <span id="doisPontos1"></span>
                    <span id="Tiago" class="code-green"></span>
                    <span id="virgula1"></span>
                  </p>
                  <p>
                    <span id="age" class="code-red"></span>
                    <span id="doisPontos2"></span>
                    <span id="idade" class="code-orange"></span>
                    <span id="virgula2"></span>
                  </p>
                  <p>
                    <span id="role" class="code-red"></span>
                    <span id="doisPontos3"></span>
                    <span id="fullstack" class="code-green"></span>
                    <span id="virgula3"></span>
                  </p>
                  <p>
                    <span id="git" class="code-red"></span>
                    <span id="doisPontos4"></span>
                    <span class="code-green"><a href="https://github.com/MrValraven" target="_blank" id="githubLink" class="code-green"></a></span>
                    <span id="virgula4"></span>
                  </p>
                  <p>
                    <span id="IDE" class="code-red"></span>
                    <span id="doisPontos5"></span>
                    <span id="vscode" class="code-green"></span>
                  </p>
                  <p>
                    <span id="chavetas2" class="code-purple"></span>
                  </p>
                  <p class="blankSpace">&nbsp;</p>
                  <p>
                    <span id="class" class="code-purple"></span>
                    <span id="toolset" class="code-yellow"></span>
                    <span id="chavetas3" class="code-purple"></span>
                  </p>
                  <p>
                    <span id="skills" class="code-red"></span>
                    <span id="doisPontos6"></span>
                    <span id="chavetas4" class="code-purple"></span>
                    <span id="icon1" class="code-red"></span>
                    <span id="doisPontos7"></span>
                    <span id="string1" class="code-yellow"></span>
                    <span id="virgula4"></span>
                    <span id="name2" class="code-red"></span>
                    <span id="doisPontos8"></span>
                    <span id="string2" class="code-yellow"></span>
                    <span id="chavetas5" class="code-purple"></span>
                    <span id="array1" class="code-purple"></span>
                    <span id="array2" class="code-purple"></span>
                    <span id="pontovirgula1"></span>
                  </p>
                  <p class="blankSpace">&nbsp;</p>
                  <p>
                    <span id="constructor" class="code-yellow"></span>
                    <span id="parenteses1" class="code-purple"></span>
                    <span id="skillset" class="code-red"></span>
                    <span id="doisPontos9" class="code-red"></span>
                    <span id="chavetas6" class="code-purple"></span>
                    <span id="icon2" class="code-red"></span>
                    <span id="doisPontos10"></span>
                    <span id="string3" class="code-yellow"></span>
                    <span id="virgula5"></span>
                    <span id="name3" class="code-red"></span>
                    <span id="doisPontos11"></span>
                    <span id="string4" class="code-yellow"></span>
                    <span id="chavetas7" class="code-purple"></span>
                    <span id="array3" class="code-purple"></span>
                    <span id="array4" class="code-purple"></span>
                    <span id="parenteses2" class="code-purple"></span>
                    <span id="chavetas8" class="code-purple"></span>
                  </p>
                  <p>
                    <span id="this1" class="code-yellow"></span>
                    <span id="ponto1"></span>
                    <span id="skills2" class="code-red"></span>
                    <span id="ponto2"></span>
                    <span id="push" class="code-blue"></span>
                    <span id="parenteses3" class="code-blue"></span>
                    <span id="reticencias"></span>
                    <span id="skillset2" class="code-red"></span>
                    <span id="parenteses4" class="code-blue"></span>
                    <span id="pontovirgula2"></span>
                  </p>
                  <p><span id="chavetas9" class="code-purple"></span></p>
                  <p class="blankSpace">&nbsp;</p>
                  <p>
                    <span id="display" class="code-blue"></span>
                    <span id="parenteses5" class="code-blue"></span>
                    <span id="parenteses6" class="code-blue"></span> 
                    <span id="chavetas10" class="code-purple"></span>
                  </p>
                  <p>
                    <span id="for" class="code-blue"></span>
                    <span id="parenteses7" class="code-blue"></span>
                    <span id="let" class="code-purple"></span>
                    <span id="skill1" class="code-red"></span>
                    <span id="in" class="code-purple"></span>
                    <span id="this2" class="code-yellow"></span>
                    <span id="ponto3"></span>
                    <span id="skills3" class="code-red"></span>
                    <span id="parenteses8" class="code-blue"></span>
                    <span id="chavetas11" class="code-blue"></span>
                  </p>
                  <p>
                    <span id="console" class="code-yellow"></span>
                    <span id="ponto4"></span>
                    <span id="log" class="code-blue"></span>
                    <span id="parenteses9" class="code-blue"></span>
                    <span id="skill2" class="code-red"></span>
                    <span id="parenteses20" class="code-blue"></span>
                    <span id="pontovirgula3"></span>
                  </p>
                  <p><span id="chavetas12" class="code-blue"></span></p>
                  <p><span id="chavetas13" class="code-purple"></span></p>
                  <p><span id="chavetas14" class="code-yellow"></span></p>
                  <p>&nbsp;</p>
                  <p>
                    <span id="export" class="code-purple"></span>
                    <span id="chavetas15" class="code-yellow"></span>
                    <span id="toolset2" class="code-yellow"></span>
                    <span id="chavetas16" class="code-yellow"></span>
                    <span id="pontovirgula4"></span>
                    </p>
                </div>
              </div>
          </div>
        </div>
        <div class="toolset">

          <h1 class="title">main.ts - portefolio - Visual Studio Code</h1>
          <h1 class="file">
            <span>
              <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 48 48" width="20px" height="20px"><rect width="36" height="36" x="6" y="6" fill="#1976d2"/><polygon fill="#fff" points="27.49,22 14.227,22 14.227,25.264 18.984,25.264 18.984,40 22.753,40 22.753,25.264 27.49,25.264"/><path fill="#fff" d="M39.194,26.084c0,0-1.787-1.192-3.807-1.192s-2.747,0.96-2.747,1.986 c0,2.648,7.381,2.383,7.381,7.712c0,8.209-11.254,4.568-11.254,4.568V35.22c0,0,2.152,1.622,4.733,1.622s2.483-1.688,2.483-1.92 c0-2.449-7.315-2.449-7.315-7.878c0-7.381,10.658-4.469,10.658-4.469L39.194,26.084z"/></svg>
              main.ts 
              <i class="fas fa-times"></i>
              </span>
            </h1>
          <h2>src <i class="fas fa-chevron-right"></i> main.ts</h2>

          <div class="editor">
            <div class="lineNumbers">
              <li>0</li>
              <li>1</li>
              <li>2</li>
              <li>3</li>
              <li>4</li>
              <li>5</li>
            </div>
            <div class="finalCode">
              <p class="toolCode">
                <span id="import" class="code-purple"></span>
                <span id="chavetas17" class="code-yellow"></span>
                <span id="toolset4" class="code-red"></span>
                <span id="chavetas18" class="code-yellow"></span> 
                <span id="from" class="code-purple"></span> 
                <span id="home" class="code-green"></span> 
                <span id="pontovirgula5" class="code-purple"></span> 
              </p>
              <p class="toolCode">
                <span id="const2" class="code-purple"></span>
                <span id="toolset5" class="code-red"></span>
                <span id="igual2"></span>
                <span id="new" class="code-purple"></span> 
                <span id="toolset6" class="code-yellow"></span>
                <span id="parenteses21" class="code-purple"></span>
                <span id="currentSkills" class="code-red"></span>
                <span id="parenteses22" class="code-purple"></span>
                <span id="pontovirgula6"></span>
              </p>
              <p class="toolCode">
                <span id="toolsetFinal" class="code-red"></span>
                <span id="ponto5" class="code-purple"></span>
                <span id="display2" class="code-blue"></span>
                <span id="pontovirgula7"></span>
              </p>
            </div>
          </div>
          <div :class="{terminalOn: codeEnd}" class="terminal">
            <p :class="{terminalOnOptions: codeEnd}" class="terminalOptions">Problems Output Debug Console <span>Terminal</span></p>
            <p class="toolCode lastp"></p>
          </div>
          
          <ul>
            <li :class="{html: codeEnd}">
              <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 32 32"><path d="M21.963,11.481l-9.457-0.008l0.224,2.531l9.006,0.007l-0.684,7.587l-5.066,1.4L15.981,23l-5.061-1.409l-0.351-3.968l2.481,0.002l0.182,2.059l2.752,0.746l0.003-0.001v0l2.756-0.741l0.289-3.205l-3.042-0.002l-5.523-0.004L9.807,9l6.19,0.005l6.19,0.005L21.963,11.481z"/><path fill="none" stroke="#ffffff" stroke-miterlimit="10" stroke-width="2" d="M6.309,5l1.749,19.795L15.977,27l7.93-2.191l1.783-19.793L6.309,5z"/></svg>
              <p>HTML5</p>
            </li>
            <li :class="{css: codeEnd}">
              <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 32 32"><path d="M6,4l2,21l8,3l8-3l2-21H6z M22.391,10l-5.696,3h2.427H22h0.123l-0.512,6.007L21.631,19l-0.275,3L16,24l-5.366-2l-0.329-4 h3.021l0.157,2.034L16,20.904l2.521-0.853L18.867,16H10.13l-0.257-3l5.91-3H9.609L9.332,7h13.32L22.391,10z"/></svg>
              <p>CSS3</p>
            </li>
            <li :class="{sass: codeEnd}">
              <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 32 32"><path d="M27.534,17.792c-1.118,0.006-2.086,0.274-2.898,0.674c-0.297-0.592-0.597-1.114-0.648-1.501	c-0.059-0.452-0.127-0.722-0.056-1.261c0.071-0.539,0.383-1.302,0.378-1.359c-0.005-0.057-0.07-0.332-0.715-0.336	c-0.645-0.005-1.196,0.124-1.261,0.294c-0.065,0.17-0.189,0.553-0.266,0.953c-0.113,0.585-1.287,2.67-1.954,3.761	c-0.218-0.426-0.403-0.801-0.442-1.098c-0.059-0.452-0.127-0.722-0.056-1.261c0.071-0.539,0.383-1.302,0.378-1.359	c-0.005-0.057-0.07-0.332-0.715-0.336c-0.645-0.005-1.196,0.124-1.261,0.294c-0.065,0.17-0.134,0.568-0.266,0.953	c-0.132,0.385-1.693,3.863-2.102,4.765c-0.208,0.459-0.39,0.828-0.518,1.08c0-0.001-0.001-0.001-0.001-0.001	s-0.008,0.017-0.021,0.045c-0.11,0.215-0.175,0.333-0.175,0.333s0.001,0.002,0.002,0.004c-0.087,0.158-0.18,0.304-0.226,0.304	c-0.032,0-0.097-0.419,0.014-0.995c0.232-1.207,0.79-3.088,0.785-3.153c-0.003-0.033,0.104-0.361-0.364-0.533	c-0.455-0.167-0.617,0.111-0.659,0.112c-0.04,0.001-0.07,0.098-0.07,0.098s0.507-2.116-0.967-2.116	c-0.921,0-2.198,1.008-2.827,1.922c-0.397,0.217-1.246,0.68-2.148,1.175c-0.346,0.19-0.699,0.384-1.034,0.569	c-0.023-0.025-0.045-0.05-0.069-0.075c-1.787-1.907-5.091-3.255-4.951-5.819c0.051-0.932,0.375-3.386,6.348-6.362	c4.893-2.438,8.81-1.767,9.487-0.28c0.967,2.124-2.094,6.073-7.175,6.642c-1.936,0.217-2.955-0.533-3.209-0.813	c-0.267-0.294-0.307-0.307-0.406-0.252c-0.162,0.09-0.059,0.35,0,0.504c0.152,0.395,0.774,1.095,1.836,1.443	c0.934,0.306,3.207,0.475,5.956-0.589c3.079-1.191,5.483-4.504,4.777-7.273c-0.718-2.816-5.388-3.742-9.808-2.172	C7.597,5.708,4.749,7.175,2.702,9.09c-2.434,2.277-2.823,4.259-2.663,5.087c0.568,2.942,4.624,4.858,6.248,6.278	c-0.08,0.044-0.155,0.086-0.224,0.123c-0.814,0.403-3.905,2.021-4.679,3.73c-0.877,1.939,0.14,3.33,0.813,3.517	c2.086,0.58,4.226-0.464,5.376-2.179c1.15-1.715,1.009-3.948,0.482-4.968c-0.007-0.013-0.014-0.025-0.021-0.038	c0.21-0.124,0.425-0.251,0.637-0.376c0.414-0.243,0.821-0.47,1.174-0.662c-0.197,0.541-0.342,1.19-0.417,2.127	c-0.088,1.101,0.363,2.523,0.953,3.083c0.26,0.246,0.573,0.252,0.771,0.252c0.687,0,1-0.571,1.345-1.247	c0.423-0.829,0.799-1.794,0.799-1.794s-0.471,2.606,0.813,2.606c0.468,0,0.939-0.607,1.148-0.916	c0.001,0.003,0.001,0.005,0.001,0.005s0.012-0.02,0.036-0.061c0.049-0.074,0.076-0.122,0.076-0.122s0.001-0.005,0.002-0.013	c0.188-0.327,0.605-1.071,1.231-2.299c0.808-1.586,1.583-3.573,1.583-3.573s0.072,0.486,0.308,1.289	c0.139,0.473,0.434,0.995,0.667,1.496c-0.187,0.26-0.303,0.41-0.303,0.41s0.001,0.003,0.003,0.008	c-0.15,0.199-0.318,0.414-0.494,0.623c-0.638,0.76-1.398,1.627-1.499,1.878c-0.12,0.295-0.092,0.512,0.14,0.687	c0.169,0.128,0.47,0.147,0.785,0.126c0.573-0.039,0.977-0.181,1.176-0.267c0.31-0.11,0.671-0.282,1.011-0.531	c0.626-0.46,1.003-1.118,0.967-1.99c-0.02-0.48-0.173-0.957-0.367-1.406c0.057-0.082,0.114-0.164,0.171-0.247	c0.987-1.442,1.752-3.027,1.752-3.027s0.072,0.486,0.308,1.289c0.12,0.407,0.355,0.85,0.567,1.285	c-0.928,0.754-1.503,1.629-1.703,2.204c-0.369,1.063-0.08,1.544,0.462,1.654c0.246,0.05,0.593-0.063,0.854-0.173	c0.325-0.108,0.715-0.287,1.08-0.555c0.626-0.46,1.227-1.104,1.191-1.976c-0.017-0.397-0.124-0.791-0.27-1.169	c0.786-0.328,1.804-0.51,3.101-0.358c2.782,0.325,3.327,2.062,3.223,2.789c-0.104,0.727-0.688,1.127-0.883,1.247	c-0.195,0.121-0.255,0.163-0.238,0.252c0.024,0.13,0.114,0.125,0.28,0.097c0.229-0.039,1.461-0.591,1.513-1.933	C32.057,19.648,30.425,17.777,27.534,17.792z M6.093,25.021c-0.921,1.005-2.209,1.385-2.761,1.065	c-0.596-0.346-0.36-1.825,0.771-2.892c0.689-0.65,1.579-1.249,2.169-1.618c0.134-0.081,0.332-0.2,0.571-0.343	c0.04-0.023,0.062-0.035,0.062-0.035l-0.001-0.001c0.046-0.028,0.094-0.056,0.143-0.085C7.459,22.629,7.06,23.966,6.093,25.021z M12.805,20.457c-0.321,0.782-0.993,2.784-1.401,2.677c-0.351-0.092-0.565-1.614-0.07-3.111c0.249-0.754,0.781-1.654,1.093-2.004	c0.503-0.563,1.057-0.747,1.191-0.518C13.789,17.791,13.006,19.967,12.805,20.457z M18.351,23.103	c-0.136,0.071-0.261,0.116-0.319,0.081c-0.043-0.025,0.056-0.119,0.056-0.119s0.694-0.746,0.967-1.086	c0.159-0.198,0.343-0.432,0.544-0.695c0.002,0.026,0.003,0.052,0.003,0.078C19.599,22.257,18.736,22.861,18.351,23.103z M22.623,22.13c-0.101-0.072-0.085-0.306,0.249-1.033c0.131-0.286,0.43-0.766,0.95-1.225c0.06,0.189,0.097,0.37,0.096,0.539	C23.911,21.535,23.108,21.955,22.623,22.13z"/></svg>
              <p>SASS</p>
            </li>
            <li :class="{js: codeEnd}">
              <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 32 32"><path d="M23,20.767C23,22.211,21.86,23,20.34,23c-1.492,0-2.461-0.713-2.926-1.644l1.311-0.751 c0.342,0.561,0.789,0.979,1.577,0.979c0.665,0,1.093-0.333,1.093-0.798c0-0.551-0.437-0.741-1.169-1.064l-0.399-0.171 c-1.159-0.494-1.929-1.121-1.929-2.432c0-1.207,0.922-2.119,2.347-2.119c1.026,0,1.758,0.352,2.29,1.283L21.28,17.09 c-0.276-0.494-0.57-0.694-1.036-0.694c-0.475,0-0.77,0.304-0.77,0.694c0,0.475,0.295,0.675,0.988,0.979l0.399,0.171 C22.23,18.819,23,19.418,23,20.767z"/><path d="M16,15.095v5.482C16,22.24,15.021,23,13.596,23c-1.283,0-2.033-0.665-2.413-1.473l1.311-0.789 c0.247,0.447,0.485,0.827,1.036,0.827c0.523,0,0.865-0.209,0.865-1.007v-5.463H16z"/><path d="M5,5v22h22V5H5z M7,7h18v18H7V7z"/></svg>
              <p>Javascript</p>
            </li>
            <li :class="{ts: codeEnd}">
              <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 32 32" ><rect width="22" height="22" x="5" y="5" fill="none" stroke="#ffffff" stroke-miterlimit="10" stroke-width="2"/><polygon points="17.588,14 10.325,14 10.325,15.873 12.879,15.873 12.879,24.016 14.98,24.016 14.98,15.873 17.588,15.873"/><path d="M23.547,16.373c0,0-0.978-0.652-2.083-0.652c-1.105,0-1.503,0.525-1.503,1.087c0,1.449,4.039,1.304,4.039,4.22	c0,4.492-6.158,2.5-6.158,2.5v-2.155c0,0,1.177,0.888,2.59,0.888s1.358-0.924,1.358-1.051c0-1.34-4.003-1.34-4.003-4.311	c0-4.039,5.832-2.445,5.832-2.445L23.547,16.373z"/></svg>
              <p>Typescript</p>
            </li>
            <li :class="{vue: codeEnd}">
              <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 32 32"><path d="M25.5,8L16,24.1L6.5,8h5.3l2.4,4.2l1.7,3l1.7-3L20.2,8H25.5 M29,6H19l-3,5.3L13,6H3l13,22L29,6L29,6z"/><polygon points="19.6,7 16,12 12.4,7 9.7,7 16,18 22.3,7"/><polygon points="19.6,7 16,12 12.4,7 9.7,7 16,18 22.3,7"/></svg>
              <p>Vue.js</p>
            </li>
            <li :class="{node: codeEnd}">
              <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 32 32"><path d="M26.96,9l-9.92-5.73c-0.63-0.36-1.46-0.36-2.09,0L5.04,8.99C4.4,9.36,4,10.06,4,10.8v10.38c0,0.75,0.4,1.44,1.04,1.81 l2.6,1.5c1.26,0.62,1.71,0.62,2.28,0.62c1.87,0,2.94-1.13,2.94-3.09V11.31c0-0.16-0.13-0.29-0.29-0.29h-1.25 c-0.17,0-0.29,0.13-0.29,0.29v10.7c0,0.88-0.91,1.74-2.38,1.01l-2.72-1.57c-0.1-0.05-0.16-0.16-0.16-0.27V10.81 c0-0.12,0.06-0.22,0.16-0.28l9.91-5.72c0.09-0.06,0.21-0.06,0.31,0l9.91,5.72c0.1,0.06,0.16,0.16,0.16,0.27v10.38 c0,0.11-0.06,0.22-0.15,0.27l-9.92,5.73c-0.09,0.05-0.22,0.05-0.31,0l-2.55-1.51c-0.07-0.05-0.17-0.06-0.24-0.02 c-0.71,0.4-0.84,0.45-1.5,0.68c-0.16,0.05-0.41,0.15,0.09,0.43l3.31,1.96C15.27,28.9,15.63,29,15.99,29c0.37,0,0.73-0.1,1.05-0.28 l9.92-5.73C27.6,22.62,28,21.93,28,21.18V10.81C28,10.06,27.6,9.37,26.96,9z"/><path d="M24,18.595c0,2.16-1.8,3.4-4.94,3.4c-4.34,0-5.25-1.99-5.25-3.66c0-0.15,0.12-0.28,0.28-0.28h1.29 c0.14,0,0.26,0.1,0.28,0.24c0.19,1.3,0.77,1.96,3.4,1.96c2.09,0,2.98-0.47,2.98-1.57c0-0.64-0.25-1.12-3.5-1.44 c-2.72-0.27-4.4-0.87-4.4-3.04c0-2,1.69-3.2,4.52-3.2c3.18,0,4.75,1.11,4.95,3.47c0.01,0.09-0.02,0.17-0.07,0.22 c-0.06,0.06-0.13,0.1-0.21,0.1h-1.29c-0.14,0-0.25-0.1-0.28-0.23c-0.31-1.37-1.07-1.81-3.1-1.81c-2.28,0-2.55,0.79-2.55,1.39 c0,0.72,0.31,0.93,3.4,1.33C22.55,15.885,24,16.455,24,18.595z"/></svg>
              <p>Node.js</p>
            </li>
            <li :class="{npm: codeEnd}">
              <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 32 32"><path d="M16,17.667h-1.778v-4.111H16V17.667z M32,10v11H16v2H9v-2H0V10H32z M8.889,11.778H1.778v7.667h3.556v-5.889h1.778v5.889 h1.778V11.778z M17.778,11.778h-7.111v9.444h3.556v-1.778h3.556V11.778z M30.222,11.778H19.556v7.667h3.556v-5.889h1.778v5.889 h1.778v-5.889h1.778v5.889h1.778V11.778z"/></svg>
              <p>Npm</p>
            </li>
            <li :class="{yarn: codeEnd}">
              <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 32 32"><path d="M22.6,20.2c-1.8,0.4-2.3,1.5-4.9,2.2c0,0-0.1,0.2-0.5,0.3c-0.6,0.2-3,0.3-3.2,0.3c-0.6,0-0.9-0.2-1-0.4 c-0.3-0.7,0.4-1,0.4-1c-0.4-0.2-0.4-0.5-0.5-0.4c-0.1,0.3-0.2,0.9-0.5,1.2c-0.4,0.4-1.2,0.3-1.7,0c-0.5-0.2,0-0.8,0-0.9 c-0.1,0-0.3,0.1-0.5-0.2c-0.3-0.4-0.8-1.8,0.5-2.9c-0.1-0.5-0.2-2.5,1.9-4c0,0-1-1.1-0.6-2c0.2-0.6,0.3-0.6,0.4-0.7 c0.3-0.1,0.5-0.2,0.7-0.4c1-1,2.2-0.8,2.2-0.8s0.6-1.8,1.1-1.4c0.2,0.1,0.8,1.4,0.8,1.4s0.6-0.4,0.7-0.2c0.4,0.7,0.4,2.2,0.3,3.1 c-0.3,1.4-1,2.2-1.3,2.7c-0.1,0.1,0.8,0.5,1.3,1.9c0.5,1.3,0,2.5,0.1,2.6c0,0.1,0.7,0,1.7-0.6c0.6-0.4,1.3-0.8,2.1-0.8 C23.2,19.1,23.2,20.1,22.6,20.2z"/><path d="M16,29C8.8,29,3,23.2,3,16S8.8,3,16,3s13,5.8,13,13S23.2,29,16,29z M16,5C9.9,5,5,9.9,5,16s4.9,11,11,11 s11-4.9,11-11S22.1,5,16,5z"/></svg>
              <p>Yarn</p>
            </li>
            <li :class="{gitalt: codeEnd}">
              <i class="fab fa-git-alt"></i>
              <p>Git</p>
            </li>
            <li :class="{sql: codeEnd}">
              <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 32 32"><path d="M17.582,5.996C17.582,5.996,17.582,5.996,17.582,5.996C17.582,5.996,17.582,5.996,17.582,5.996 M17.581,5.996C21.946,6.065,23,8.614,23,10c-1.257,0.105-2.306,0.159-2.77,0.898c-1.059,1.687-0.266,4.538,0.478,5.822c0.08,0.138,0.946,0.957,1.292,1.28c0.126,0.118-0.46,0.276-0.58,0.4c-0.335,0.348-0.33,1.401-0.4,2.587C21.007,20.995,21,21,21,21s0.005,0.11,0.011,0.261C21.008,21.374,21,21.477,21,21.6v2.016C21,26.124,19.603,27,18.438,27c-1.237,0-2.302-1.01-2.302-1.867c0-0.503-0.081-1.362-0.136-2.133c0.013-1.777,0-2.422,0-3c0-0.559-1-1-1-1c0.125-0.292,0.53-0.892,0.53-0.892C15.834,17.351,15.994,16.631,16,15c0.003-0.746-0.098-1.56-0.309-2.491C15.403,11.24,14.44,10.01,13,10c-0.009,0-0.018,0-0.027,0c-0.585,0-0.515,0-0.973,0C12,8,14.665,5.996,17.581,5.996 M17.581,5.996C17.581,5.996,17.581,5.996,17.581,5.996C17.581,5.996,17.581,5.996,17.581,5.996 M17.581,3.996C13.543,3.996,10,6.802,10,10c0,1.105,0.895,2,2,2l0.42,0l0.553,0c0.385,0.003,0.678,0.558,0.767,0.951c0.177,0.781,0.262,1.449,0.26,2.041c-0.005,1.271-0.111,1.784-0.259,2.194c-0.192,0.295-0.441,0.702-0.58,1.026c-0.404,0.942-0.028,2.024,0.842,2.522c0.003,0.482,0.005,1.145-0.003,2.251c0,0.052,0.001,0.105,0.005,0.157l0.048,0.637c0.041,0.522,0.083,1.062,0.083,1.353c0,2.024,2.051,3.867,4.302,3.867C20.635,29,23,27.315,23,23.616V21.6c0-0.048,0.003-0.091,0.004-0.134l0.006-0.144c0.001-0.045,0.001-0.089,0-0.134c0.003-0.028,0.005-0.056,0.007-0.085l0.029-0.548c0.012-0.25,0.028-0.554,0.048-0.802c0.375-0.261,0.784-0.69,0.898-1.392c0.107-0.659-0.14-1.369-0.628-1.824c-0.401-0.373-0.816-0.774-1.008-0.97c-0.514-0.993-0.819-2.632-0.52-3.425c0.273-0.061,0.776-0.103,1.163-0.135l0.168-0.014C24.203,11.907,25,11.04,25,10c0-2.036-1.544-5.911-7.387-6.003C17.602,3.997,17.592,3.996,17.581,3.996L17.581,3.996z"/><path d="M9.325 4.994c1.339 0 2.361.294 3.271.636-2.15 1.019-2.595 3.163-2.595 5.369 0 .002.001.004.001.006 0 .005-.002.009-.002.014-.001.088.029.247.029.462C10.029 12.5 10 14.71 10 16c0 2.201 2.352 4.003 2.962 4.003.014 0 .026-.001.038-.003-1.167.667-2.917 1-3.999 1C6.347 21 5.086 11.638 5 10 4.771 5.636 6.646 5.082 9 5 9.111 4.996 9.219 4.994 9.325 4.994M9.325 2.994C9.325 2.994 9.324 2.994 9.325 2.994c-.13 0-.261.002-.395.007-1.517.053-3.237.292-4.5 1.67-1.09 1.189-1.557 2.967-1.428 5.433.047.888.388 3.76 1.098 6.51C4.809 19.355 6.088 23 9.001 23c1.384 0 3.465-.391 4.992-1.263.837-.478 1.214-1.486.896-2.396-.242-.693-.835-1.18-1.525-1.308C12.93 17.757 12 16.831 12 16c0-.678.008-1.613.016-2.492.007-.794.013-1.543.013-2.026 0-.203-.015-.374-.028-.51 0-.009 0-.017-.001-.026.01-2.482.703-3.153 1.452-3.508.726-.344 1.175-1.088 1.142-1.89C14.561 4.745 14.051 4.04 13.3 3.758 12.353 3.402 11.046 2.994 9.325 2.994L9.325 2.994zM22.605 4.972c.985 0 2.925.199 3.893 1.654C27.713 8.455 26.542 18.417 23 19c.917-.292 1.833-.292 2-3 0-.833-.046-3.619 0-4 .063-.518.019-1.448 0-2 .015-.073.014-.152.014-.245C25.014 6.912 22 5 22 5S22.235 4.972 22.605 4.972M22.605 2.972c-.464 0-.781.035-.84.042-.84.1-1.527.717-1.715 1.542-.188.825.164 1.679.879 2.132.011.008 2.085 1.404 2.085 3.066 0 0 0 .005 0 .011-.012.1-.016.202-.012.303l.007.194c.014.386.044 1.189.007 1.494-.04.325-.044.948-.023 3.176C22.996 15.379 23 15.767 23 16c0 .577.171.927 0 1l-.75 1.5c-.154.308-.209.657-.158.999C22.205 20.266 22.25 21 22.997 21c.108 0 .218-.009.328-.027 1.19-.196 2.873-1.038 4.133-3.933 1.489-3.423 2.107-9.412.704-11.521C26.689 3.303 24.048 2.972 22.605 2.972L22.605 2.972z"/><path d="M26.36 20.126c-1.501.359-2.223.168-2.573-.082-.056.047-2.85-.625-1.788 2 .047.01 1.384-.004 1.384-.004.744.039 1.717-.202 2.288-.51C26.902 20.867 27.573 19.836 26.36 20.126zM13.878 12.71C13.675 12.891 13.354 13.049 13 13c-.576-.08-1.018-.68-.987-.904h0c.03-.224.523-.341 1.099-.261.2.028.382.077.535.137C14.056 12.149 14.102 12.441 13.878 12.71zM21.133 12.701c.203.181.525.34.878.29.576-.08 1.018-.68.987-.904h0c-.03-.224-.523-.341-1.099-.261-.2.028-.382.077-.535.137C20.956 12.14 20.909 12.432 21.133 12.701zM18 4c0 0 1.125-1 4-1s-1 2-1 2S18.688 4.688 18 4zM16 5c0 0-2.417-2-7-2v1l5 2L16 5z"/></svg>
              <p>PostgresSQL</p>
            </li>
          </ul>
        </div>
        
      </section>
      <section id="build" v-if="finished">
        <h2 class="comments">/**</h2>
        <h1 class="comments">* Made with</h1>
        <h2 class="comments">**/</h2>
        <div class="builtWith">
          <ul>
            <h2><i class="fas fa-code"></i></h2>
            <li>14 SVGs</li>
            <li>58 hours of work</li>
            <li>102 hours of thinking</li>
            <li>354 lines of JS</li>
            <li>601 lines of HTML</li>
            <li>1007 lines of SCSS</li>
          </ul>
          <ul class="music" :style="{color: darkBlue}">
            <h2><i class="fas fa-music"></i></h2>
            <li><a :style="{color: darkBlue}" rel="noopener noreferrer" target="_blank" href="https://open.spotify.com/artist/0L8ExT028jH3ddEcZwqJJ5?si=q1xvTHkkTTWSqvP52sFmmg&dl_branch=1">Red Hot Chilli Peppers</a></li>
            <li><a :style="{color: darkBlue}" rel="noopener noreferrer" target="_blank" href="https://open.spotify.com/artist/3MATPJ9tYbcMhw5VOZrRU6?si=RDo3zv7hSxKVNnuAvwspHQ&dl_branch=1">Summer Salt</a></li>
            <li><a :style="{color: darkBlue}" rel="noopener noreferrer" target="_blank" href="https://open.spotify.com/artist/7wbkl3zgDZEoZer357mVIw?si=Cm5BTNqzRbGlgq0XdUa_ZQ&dl_branch=1">Boy Pablo</a></li>
            <li><a :style="{color: darkBlue}" rel="noopener noreferrer" target="_blank" href="https://open.spotify.com/artist/3BR3Qfra04DICDUB2BL3eu?si=KGtSyrWOSwKLXpcy-Z65EQ&dl_branch=1">Men on the couch</a></li>
            <li><a :style="{color: darkBlue}" rel="noopener noreferrer" target="_blank" href="https://open.spotify.com/artist/5p0zkKpBuRguKebwRe0RI2?si=bMgvegk3R6G10ZP6f7kvGg&dl_branch=1">Pierce Fulton</a></li>
            <li><a :style="{color: darkBlue}" rel="noopener noreferrer" target="_blank" href="https://open.spotify.com/artist/2SdOKxC1sSxEyv8JYERaNe?si=khNCyTwzRwmGyZXaXDWdqA&dl_branch=1">RuPaul</a></li>
          </ul>
          <ul class="food">
            <h2><i class="fas fa-battery-three-quarters"></i></h2>
            <li>1 glass of wine</li>
            <li>7 pizzas</li>
            <li>37 gigatons of Hummus</li>
            <li>47 vegan chocolate cookies</li>
            <li>85 Chleb</li>
            <li>∞ fresh vegetables</li>
          </ul>
        </div>
       
      </section>
      <section class="contacts">
        <h1 :style="{backgroundColor: white} ">Let's create cool things together</h1>
        <h3 :style="{backgroundColor: white} ">Stay creative and have a stunning {{ weekDayOfToday }}!</h3>
        <div class="content" :style="{backgroundColor: white} ">
          <div class="cta">
            <video id="video" autoplay="true" muted="true" loop="true">
              <source src="@/assets/brofist.mp4"
                      type="video/mp4" />
            </video>
          </div>
          <div class="socials">
              <a  class="github" href="https://github.com/MrValraven" target="_blank"  :style="{color: darkBlue} ">
                <i id="github" class="fab fa-github" :style="{color: darkBlue} "></i>
                <p>@MrValraven</p>
              </a>
              <a class="linkedInA" href="https://www.linkedin.com/in/tiago-costa-b141121b1/" target="_blank" :style="{color: darkBlue} ">
                <i id="linkedin" class="fab fa-linkedin" :style="{color: darkBlue} "></i>
                <p>Tiago Costa</p>
              </a>
              <a class="discord" @click="copyDiscord" :style="{color: darkBlue} ">
                <i id="discord" class="fab fa-discord" :style="{color: darkBlue} "></i>
                <p id="discordID">Valraven#7264</p>
              </a>
          </div>
          <form @submit.prevent>
            <label for="contactName" :style="{color: darkBlue} ">Name</label>
            <input type="text" v-model="contactName" required>
            <label for="contactEmail" :style="{color: darkBlue} ">Email</label>
            <input type="text" v-model="contactEmail" required>
            <label for="contactMessage" :style="{color: darkBlue} ">Message</label>
            <textarea type="text" v-model="contactMessage"  required/>
            <Button class="contactButton" buttonText="Send message" :style="{backgroundColor: darkBlue, color: whiteBlue, borderColor: normalBlue}" />
          </form>
        </div>
        <div v-if="openNotification" class="notification"  :style="{backgroundColor: darkBlue, color: whiteBlue}" >
          <p>DiscordID copied sucessfully</p>
          <i @click="openNotification = false" class="fas fa-times"></i>
        </div>
      </section>
      <section class="frases" v-if="finished">
        <h1>video / seccao sobre todo o processo de construçao dos websites e processo criativo e tecnico</h1>
        <h1>video of myself being a retard </h1>
        <h1>It's important to think outside of the box</h1>
        <h1>show personality</h1>
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
        ]
        const chars2 = [ 
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
        return { chars, chars2, beforeEnter, enter }
    },
  data() {
    return {
      activatedNavbar: false,
      isAtTop: true,
      mobileMode: false,
      finished: false,
      isOnTeto: false,
      isOnExpo: false,
      opacityTeto: 0,
      opacityExpo: 0,
      activateTyping: true,
      codeEnd: false,
      lineNumbers: [121],
      image: 'https://i.pinimg.com/originals/e3/66/87/e366871039caf5afd17b0bcfecb453cb.jpg',
      contactName: "",
      contactEmail: "",
      contactMessage: "",
      weekDayOfToday: "",
      openNotification: false,
      isDarkMode: false,
      theme: 'light',
      whiteBlue: '#E7ECEF',
      darkBlue: '#274C77',
      normalBlue: '#6aa7cf',
      lightBlue: '#A3CEF1',
      editorBlue: '#21313c',
      gostoDesteAzul: '#aedbf7',
      white: '#FFFFFF',
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
    const currentTheme = localStorage.getItem("theme")!;
    this.checkTheme(currentTheme);
    for(let i: number = 122; i < 146; i++) {
      this.lineNumbers.push(i);
    }

    let day = new Date();
    let weekday = new Array(7);
    weekday[0] = "Sunday";
    weekday[1] = "Monday";
    weekday[2] = "Tuesday";
    weekday[3] = "Wednesday";
    weekday[4] = "Thursday";
    weekday[5] = "Friday";
    weekday[6] = "Saturday";

    this.weekDayOfToday = weekday[day.getDay()];
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

      let tetoProjectHeight = document.querySelector('.seistetos')?.getBoundingClientRect().top;
      tetoProjectHeight = Number(tetoProjectHeight);

      if(window.pageYOffset >= tetoProjectHeight - 400) {
        this.isOnTeto = true;
        this.opacityTeto = 1;
      }

      let expoProjectHeight = document.querySelector('.expoestudante')?.getBoundingClientRect().top;
      expoProjectHeight = Number(expoProjectHeight);

      if(window.pageYOffset >= expoProjectHeight + 200) {
        this.isOnExpo = true;
        this.opacityExpo = 1;
      }

      let aboutMeHeight = document.querySelector('.aboutMe')?.getBoundingClientRect().top;
      aboutMeHeight = Number(aboutMeHeight);

      if(aboutMeHeight < 650 && this.activateTyping) {
        this.typeAllCode();
        this.activateTyping = false;
      }
    },
    handleResize () {
      this.mobileMode = window.innerWidth <= 1015;
      if(!this.mobileMode) {
        this.activatedNavbar = false;
      }
    },

    async sleepNow(delay: number) {
      return new Promise((resolve) => setTimeout(resolve,delay));
    },

    async typeCode(element: string, word: string) {
      let selectedElement = document.querySelector(element)!;

      let index = 0;
      let maxIndex = word.length;
      let letter = "";

      while(index <= maxIndex) {
        await this.sleepNow(20);
        letter = word.slice(0, index);
        selectedElement.textContent = letter;
        index++;
      }
    },

    async typeAllCode() {

      let delay = 150;

      let arrayOfElements = [
        {element: '.const', text: 'const'},
        {element: '#me', text: ' me'},
        {element: '#igual1', text: ' = '},
        {element: '#chavetas1', text: '{'},
        {element: '#nome', text: 'name'},
        {element: '#doisPontos1', text: ': '},
        {element: '#Tiago', text: '"Tiago"'},
        {element: '#virgula1', text: ','},
        {element: '#age', text: 'age'},
        {element: '#doisPontos2', text: ': '},
        {element: '#idade', text: '22'},
        {element: '#virgula2', text: ','},
        {element: '#role', text: 'role'},
        {element: '#doisPontos3', text: ': '},
        {element: '#fullstack', text: '"Fullstack Developer"'},
        {element: '#virgula3', text: ','},
        {element: '#git', text: 'github'},
        {element: '#doisPontos4', text: ': '},
        {element: '#githubLink', text: '"https://github.com/MrValraven"'},
        {element: '#virgula4', text: ','},
        {element: '#IDE', text: 'IDE'},
        {element: '#doisPontos5', text: ': '},
        {element: '#vscode', text: '"Visual Studio Code"'},
        {element: '#chavetas2', text: '}'},
        {element: '#class', text: 'class'},
        {element: '#toolset', text: ' Toolset'},
        {element: '#chavetas3', text: ' {'},
        {element: '#skills', text: 'skills'},
        {element: '#doisPontos6', text: ': '},
        {element: '#chavetas4', text: ' {'},
        {element: '#icon1', text: ' icon'},
        {element: '#doisPontos7', text: ': '},
        {element: '#string1', text: 'string'},
        {element: '#virgula4', text: ','},
        {element: '#name2', text: ' name'},
        {element: '#doisPontos8', text: ': '},
        {element: '#string2', text: 'string'},
        {element: '#chavetas5', text: ' }'},
        {element: '#array1', text: '['},
        {element: '#array2', text: ']'},
        {element: '#pontovirgula1', text: ';'},
        {element: '#constructor', text: 'constructor'},
        {element: '#parenteses1', text: '('},
        {element: '#skillset', text: 'skillset'},
        {element: '#doisPontos9', text: ':'},
        {element: '#chavetas6', text: ' {'},
        {element: '#icon2', text: ' icon'},
        {element: '#doisPontos10', text: ': '},
        {element: '#string3', text: 'string'},
        {element: '#virgula5', text: ','},
        {element: '#name3', text: ' name'},
        {element: '#doisPontos11', text: ': '},
        {element: '#string4', text: 'string'},
        {element: '#chavetas7', text: ' }'},
        {element: '#array3', text: '['},
        {element: '#array4', text: ']'},
        {element: '#parenteses2', text: ')'},
        {element: '#chavetas8', text: ' {'},
        {element: '#this1', text: ' this'},
        {element: '#ponto1', text: '.'},
        {element: '#skills2', text: 'skills'},
        {element: '#ponto2', text: '.'},
        {element: '#push', text: 'push'},
        {element: '#parenteses3', text: '('},
        {element: '#reticencias', text: '...'},
        {element: '#skillset2', text: 'skillset'},
        {element: '#parenteses4', text: ')'},
        {element: '#pontovirgula2', text: ';'},
        {element: '#chavetas9', text: ' {'},
        {element: '#display', text: 'display'},
        {element: '#parenteses5', text: '('},
        {element: '#parenteses6', text: ')'},
        {element: '#chavetas10', text: ' {'},
        {element: '#for', text: 'for'},
        {element: '#parenteses7', text: '('},
        {element: '#let', text: 'let '},
        {element: '#skill1', text: 'skill '},
        {element: '#in', text: 'in '},
        {element: '#this2', text: 'this'},
        {element: '#ponto3', text: '.'},
        {element: '#skills3', text: 'skills'},
        {element: '#parenteses8', text: ')'},
        {element: '#chavetas11', text: ' {'},
        {element: '#console', text: 'console'},
        {element: '#ponto4', text: '.'},
        {element: '#log', text: 'log'},
        {element: '#parenteses9', text: '('},
        {element: '#skill2', text: 'skill'},
        {element: '#parenteses20', text: ')'},
        {element: '#pontovirgula3', text: ';'},
        {element: '#chavetas12', text: '}'},
        {element: '#chavetas13', text: '}'},
        {element: '#chavetas14', text: '}'},
        {element: '#export', text: 'export '},
        {element: '#chavetas15', text: '{'},
        {element: '#toolset2', text: ' Toolset '},
        {element: '#chavetas16', text: '}'},
        {element: '#pontovirgula4', text: ';'},
        {element: '#import', text: 'import'},
        {element: '#chavetas17', text: ' { '},
        {element: '#toolset4', text: 'Toolset'},
        {element: '#chavetas18', text: ' } '},
        {element: '#from', text: 'from '},
        {element: '#home', text: '"./Home.vue"'},
        {element: '#pontovirgula5', text: ';'},
        {element: '#const2', text: 'const '},
        {element: '#toolset5', text: 'toolset '},
        {element: '#igual2', text: '= '},
        {element: '#new', text: 'new '},
        {element: '#toolset6', text: 'Toolset'},
        {element: '#parenteses21', text: '('},
        {element: '#currentSkills', text: 'currentSkills'},
        {element: '#parenteses22', text: ')'},
        {element: '#pontovirgula6', text: ';'},
        {element: '#toolsetFinal', text: 'toolset'},
        {element: '#ponto5', text: '.'},
        {element: '#display2', text: 'display()'},
        {element: '#pontovirgula7', text: ';'},
      ]

      for(let i = 0; i < arrayOfElements.length; i++) {
        await this.typeCode( arrayOfElements[i].element, arrayOfElements[i].text);

        if(i % 4 === 0) {
          await this.sleepNow(delay);
        }
      }

      await this.sleepNow(delay);
      this.codeEnd = true;
      await this.typeCode('.lastp', 'PS C:\\Users\\tiagoCosta\\Desktop\\Trabalhos\\portefolio>')
    },
    async copyDiscord() {

      let copyText = document.getElementById("discordID")!;  

      // creating textarea of html
      let input = document.createElement("textarea");

      //adding p tag text to textarea 
      input.value = copyText.textContent!;
      document.body.appendChild(input);
      input.select();
      document.execCommand("Copy");

      // removing textarea after copy
      input.remove();

      this.openNotification = true;

      setTimeout(() => {
        this.openNotification = false;
      }, 10000);
    },
    checkTheme(theme: string) {

      if(theme === null) {
        this.theme = 'light';
      }

      else {
        this.theme = theme;
      }
      

      if(theme === 'light') {
        this.whiteBlue = '#E7ECEF';
        this.darkBlue = '#274C77';
        this.normalBlue = '#6aa7cf';
        this.lightBlue = '#A3CEF1';
        this.editorBlue = '#21313c';
        this.gostoDesteAzul = '#aedbf7';
        this.white = '#FFFFFF'
        this.isDarkMode = false;
      }

      else {
        this.whiteBlue = '#0e1720';/* '#112236'; */
        this.darkBlue = '#E7ECEF';
        this.normalBlue = '#E7ECEF';
        this.white = '#274C77';
        this.isDarkMode = true;
      }
    },
    toggleDarkMode() {
      this.theme === 'light' ? this.theme = 'dark' : this.theme = 'light';

      this.checkTheme(this.theme);

      // Finally, let's save the current preference to localStorage to keep using it
      localStorage.setItem("theme", this.theme);
    }
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

@keyframes scaleUp {
  0% {
    transform: scale(0);
  }

  100% {
    transform: scale(1);
  }
  
}

.darkIcon {
  position: absolute;
  font-size: 30px;
  top: 8px;
  left: 15px;
  padding: 5px;
  z-index: 9999;
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

.pageContent {
  $whiteBlue: #E7ECEF;
  $darkBlue: #274C77;
  $normalBlue: #6aa7cf;
  $lightBlue: #A3CEF1;
  $editorBlue: #21313c;
  $gostoDesteAzul: #aedbf7;

  $easing: cubic-bezier(0.39, 1.61, 0.89, 1.22);
  $fastEasing: cubic-bezier(0.075, 0.82, 0.165, 1);
  $delay: 0.5s;
  $h1Size: 70px;

  color: $darkBlue;
  background-color: $whiteBlue;

  transition: all 1s $fastEasing;


section {
  padding: 100px 100px 0px 100px;
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
  padding-bottom: 0;

  .mainImage {
    min-width: 55%;
    border-radius: 16px;
    margin-right: 25px;
    filter: grayscale(30%);
    box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px, rgba(0, 0, 0, 0.3) 0px 30px 60px -30px, rgba(10, 37, 64, 0.35) 0px -2px 6px 0px inset;
  }

  .projects {
    width: 100%;
    height: 100%;

    li {
      display: flex;
      position: relative;
      min-height: 70vh;
      border-bottom: 2px solid #cecccc9a;
      padding-bottom: 10vh;
      margin-bottom: 10vh;


      #hoverImg {
        position: absolute;
        height: 400px;
        left: 38.5%;
        bottom: 0%;
      }

      #hoverExpo {
        position: absolute;
        height: 300px;
        left: 37%;
        bottom: 4%;
      }

      
    }
  }
  
  

  .cardtext {
    margin-left: 5px;
    min-width: 45%;

    
    h2 {
      display: inline-flex;
      font-size: $h1Size;
      font-weight: 500;
      margin-left: -5px;
      line-height: 60px;
      overflow: hidden;

      .animate { 
        display: block;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 0.1s both;
      }
    }

     h3 {
      font-size: 16px;
      font-weight: 300;
      opacity: 0.8;
      margin-top: 20px;
      margin-bottom: 30px;
      overflow: hidden;

       .animate {
        display: block;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 0.2s forwards;
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

      .span1 {
        display: block;
        animation-delay: 0.7s !important;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 0.5s forwards;

      }
      .span2 {
        display: block;
        animation-delay: 0.8s !important;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 0.6s forwards;
        line-height: 1.4em;

      }
      .span3 {
        display: block;
        animation-delay: 0.9s !important;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 0.7s forwards;
        line-height: 1.4em;

      }
      .span4 {
        display: block;
        animation-delay: 1s !important;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 0.8s forwards;
        line-height: 1.4em;

      }
    }

    h4 {
      font-size: 25px;
      overflow: hidden;

       .animate {
        display: block;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 0.9s forwards;
      }
    }

    .tech {
      font-size: 16px;
      opacity: 0.8;
      overflow: hidden;

       .animate {
        display: block;
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 1.0s forwards;
      }
    }

    .links {
      margin-top: 30px;
      padding: 20px 0 20px 0;
      overflow: hidden;

      .link {
        transform: translate3d(0, -400%, 0);
        animation: showTopText 1s 1.1s forwards;
      }
    }
  }
}

.about {
  position: relative;
  display: flex;
  background: $editorBlue;
  padding: 0;
  padding-bottom: 10px;

  .aboutMe {
    width: 50%;
  }

  .card {
    position: relative;
    width: 100%;
    height: 700px;
    margin: 0px 20px 0 0;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-direction: column;
    background: $editorBlue;
    font-family: monospace;
    padding-bottom: 20px;
    
    overflow: hidden;

    .title {
      display: flex;
      align-items: center;
      font-size: 14px;
      color: white;
      opacity: 0.5;
      padding-top: 10px;
      padding-bottom: 10px;
      font-weight: 300;
    }

    .file {
      width: 100%;
      font-size: 16px;
      font-weight: 300;
      margin-bottom: 5px;
      color: white;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      background-color: darken($color: $editorBlue, $amount: 5%);

      span {
        font-size: 16px;
        font-weight: 300;
        height: 100%;
        padding: 10px;
        color: white;
        display: flex;
        justify-content: flex-start;
        align-items: center;
        background-color: $editorBlue;
        border-right: 1px solid black;

        &:hover {
          filter: brightness(90%);
        }

        svg {
          margin-right: 8px;
        }
      }

      .fa-times {
        margin-left: 10px;
        margin-top: 2px;
        opacity: 0.4;

        &:hover {
          cursor: pointer;
        }

        &:active {
          font-size: 14px;
        }

      }
    }

    h2 {
      width: 100%;
      padding-left: 10px;
      font-size: 14px;
      font-weight: 300;
      opacity: 0.7;
      color: white;
      

      .fa-chevron-right {
        margin: 0px 5px 0px 5px;
      }

      .fa-box {
        margin: 0px 2px 0px 5px;
        color: #15e6f5;
      }
    }

    .editor {
      display: flex;
      width: 100%;
      padding-top: 10px;

      .lineNumbers {
        min-width: 10%;

        p {
          color: white;
          opacity: 0.5;
          font-weight: 100;
          font-size: 16px;
          padding-left: 10px;
          margin: 5px 0 5px 0;

          &:first-child {
            margin-top: 0;
          }
        }
      }
    }

    .code {
      padding-left: 40px;
      min-width: 90%;

      p {
        color: white;
        font-size: 16px;
        margin: 5px 0 5px 0;

        &:first-child {
          margin-top: 0;

        }


        #class,
        #export,
        #chavetas14 {
          margin-left: -40px;
        }

        #this1,
        #for,
        #chavetas12 {
          margin-left: 40px;
        }

        #console {
          margin-left: 80px;
        }


        #githubLink {
          opacity: 1;
          text-decoration: underline;
        }

        #reticencias,
        #skillset2 {
          font-style: italic;
        }

        .code-blue {
          color: #5ca9ec;
        }

        .code-yellow {
          color: #f1d954;
        }

        .code-orange {
          color: #fa865c;
        }

        .code-purple {
          color: #d270eb;
        }

        .const,
        #chavetas2 {
          margin-left: -40px;
        }

        .code-red {
          color: #fb635b;
        }

        .code-green {
          color: #74eb70;
        }
      }
    }
  }

  .toolset {
    background-color: $editorBlue;
    border-left: 1px solid black;
    width: 50%;



    .code-blue {
      color: #5ca9ec;
    }

    .code-yellow {
      color: #f1d954;
    }

    .code-orange {
      color: #fa865c;
    }

    .code-purple {
      color: #d270eb;
    }

    .code-red {
       color: #fb635b;
    }

    .code-green {
      color: #74eb70;
    }

    .toolCode,
    .terminal .toolCode {
      margin-left: 40px;
      font-size: 16px;
      font-family: monospace;
      font-weight:  300;
      color: $whiteBlue;
    }

    .title {
      display: flex;
      align-items: center;
      font-size: 14px;
      color: white;
      opacity: 0.5;
      padding-top: 10px;
      padding-bottom: 10px;
      font-weight: 300;
      font-family: monospace;
      justify-content: center;
    }

    .file {
      width: 100%;
      font-size: 16px;
      font-weight: 300;
      font-family: monospace;
      margin-bottom: 5px;
      color: white;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      background-color: darken($color: $editorBlue, $amount: 5%);

      span {
        font-size: 16px;
        font-weight: 300;
        height: 100%;
        padding: 10px;
        color: white;
        display: flex;
        justify-content: flex-start;
        align-items: center;
        background-color: $editorBlue;
        border-right: 1px solid black;

        &:hover {
          filter: brightness(90%);
        }

        svg {
          margin-right: 8px;
        }
      }

      .fa-times {
        margin-left: 10px;
        margin-top: 2px;
        opacity: 0.4;

        &:hover {
          cursor: pointer;
        }

        &:active {
          font-size: 14px;
        }

      }
    }

    h2 {
      width: 800px;
      font-size: 14px;
      font-weight: 300;
      padding-left: 10px;
      opacity: 0.7;
      color: white;

      .fa-chevron-right {
        margin: 0px 5px 0px 5px;
      }
    }

    .editor {
      display: flex;
      padding-top: 10px;

      .lineNumbers {
        min-width: 10%;

        li {
          color: white;
          opacity: 0.5;
          font-weight: 100;
          font-size: 16px;
          padding-left: 10px;
          margin: 5px 0 5px 0;
          font-family: monospace;

          &:first-child {
            margin-top: 0;
          }
        }
      }

      .finalCode {
        min-width: 90%;
        padding-top: 5px;
        margin-top: -10px;
        margin-left: -40px;

        p {
          color: white;
          font-size: 16px;
          margin: 5px 0 5px 0;

          &:first-child {
            margin-top: 5px;
            margin-bottom: 28px;

          }
        }

        .emptyP {
          margin: 0;
        }
      }
    }

    .terminal {
      margin-top: 30px;
      color: #ffffff77;
      font-family: monospace;
      font-size: 16px;

    .terminalOptions {
      text-transform: uppercase;
      padding: 15px 10px 10px 20px;
      opacity: 0;
    }

    .lastp {
      margin-top: 30px;
      margin-left: 20px;
      opacity: 0.8;
    }

      span {
        border-bottom: 1px solid $whiteBlue;
        color: $whiteBlue;
        padding: 5px 0px;
      }
    }

    .terminalOn {
       border-top: 1px solid #ffffff77;

       .terminalOnOptions {
         opacity: 1;
       }
    }

    ul {
      display: flex;
      flex-wrap: wrap;
      margin-top: 30px;
      li {
        margin-top: 30px;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        width: 100px;
        padding: 15px 10px 15px 10px;
        margin: 0 10px 25px 10px;
        color:  $whiteBlue;
        transform: scale(0.0);

        svg {
          fill: $whiteBlue;
          width: 50px;
          height: 50px;
          opacity: 0.8;
        }

        i {
          font-size: 50px;
          margin-right: 0;
          opacity: 0.8;
        }

        p {
          opacity: 0;
          transform: translateY(5px);
          transition: opacity 0.2s cubic-bezier(0.075, 0.82, 0.165, 1), transform 0.2s cubic-bezier(0.075, 0.82, 0.165, 1);
        }

        &:hover {
          transform: scale(1);

          p {
            opacity: 1;
            transform: translateY(-1px);
          }

          svg {
            opacity: 1;
          }

          i {
            opacity: 1;
          }
        }
      }
      
      i {
        font-size: 60px;
        margin-right: 30px;
      }

      .html {
        animation: scaleUp $delay 1.5s cubic-bezier(0.075, 0.82, 0.165, 1) forwards;
      }
      .css {
        animation: scaleUp $delay 2s cubic-bezier(0.075, 0.82, 0.165, 1) forwards;
      }
      .sass {
        animation: scaleUp $delay 2.5s cubic-bezier(0.075, 0.82, 0.165, 1) forwards;
      }
      .js {
        animation: scaleUp $delay 3s cubic-bezier(0.075, 0.82, 0.165, 1) forwards;
      }
      .ts {
        animation: scaleUp $delay 3.5s cubic-bezier(0.075, 0.82, 0.165, 1) forwards;
      }
      .vue {
        animation: scaleUp $delay 4s cubic-bezier(0.075, 0.82, 0.165, 1) forwards;
      }
      .node {
        animation: scaleUp $delay 4.5s cubic-bezier(0.075, 0.82, 0.165, 1) forwards;
      }
      .npm {
        animation: scaleUp $delay 5s cubic-bezier(0.075, 0.82, 0.165, 1) forwards;
      }
      .yarn {
        animation: scaleUp $delay 5.5s cubic-bezier(0.075, 0.82, 0.165, 1) forwards;
      }
      .gitalt {
        animation: scaleUp 1s 6s cubic-bezier(0.075, 0.82, 0.165, 1) forwards;
      }
      .sql {
        animation: scaleUp 1s 6.5s cubic-bezier(0.075, 0.82, 0.165, 1) forwards;
      }

    }
  }
}


#build {



  h1 {
    font-size: $h1Size;
    font-weight: 500;
  }

  .comments {
    color: grey;
    font-size: 30px;

    &:first-child {
      margin-left: -15px;
    }
  }

  .builtWith {
    display: flex;
    justify-content: space-between;
    width: 100%;
    margin-top: 50px;

    h2 i {
      font-size: $h1Size;
      margin-bottom: 25px;
    }

    

  }
}

.contacts {
  display: flex;
  justify-content: center;
  flex-direction: column;
  padding-bottom: 100px;
  width: 100%;
  .cta {
    width: 35%;
  }

  #video {
    border-radius: 12px;
    width: 100%;
    background-color: white;
  }

  .content {
    display: flex;
    width: 100%;
    align-items: flex-start;
    background-color: white;
    padding: 25px 50px 50px 50px;
    box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
    border-radius: 0 0 12px 12px;

  }

    h1 {
      font-size: $h1Size;
      font-weight: 500;
      background-color: white;
      padding-left: 50px;
      padding-top: 25px;
      border-radius:  12px 12px 0 0;
      opacity: 1;

    }

    h3 {
      margin-top: -10px;
      padding-bottom: 10px;
      background-color: white;
      filter: grayscale(0%);
      padding-left: 60px;

    }

  form {
    display: flex;
    flex-direction: column;
    padding: 0px 0px 0 0;
    width: 45%;

    label {
      color: $darkBlue;
      font-weight: 500;
      margin-bottom: 5px;
    }

    input {
      padding: 10px;
      margin-bottom: 25px;
      border-radius: 12px;
      border: none;
      outline: none;
      background-color: $whiteBlue;
      color: $darkBlue;
    }

    textarea {
      resize: none;
      height: 100px;
      padding: 10px;
      margin-bottom: 30px;
      border-radius: 12px;
      border: none;
      outline: none;
      background-color: $whiteBlue;
      color: $darkBlue;
    }

    .contactButton {
      margin-top: 23px;
    }
  }

  .socials {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-direction: column;
    width: 20%;
    height: 400px;

    a {
      display: flex;
      justify-content: flex-start;
      align-items: center;
      flex-direction: column;
      width: 100%;
      opacity: 1;
      transition: transform 0.5s cubic-bezier(0.075, 0.82, 0.165, 1);

      &:hover {
        transform: translateY(-2px);

        i {
          color: darken($color: $normalBlue, $amount: 15%);
        }
      }

      i {
        font-size: 40px;
        padding: 5px;
        color: $darkBlue;
        transition: color 0.5s cubic-bezier(0.075, 0.82, 0.165, 1);
      }

      #github {
        padding-left: 2px;
      }
    }

    .linkedInA {
      margin: 30px 0 30px 0;
    }

    .github {
      margin: 10px 0 0px 0;
    }
  }

  .notification {
    position: fixed;
    display: flex;
    align-content: center;
    justify-content: center;
    top: 20px;
    right: 0px;
    padding: 10px;
    border-radius: 12px;
    font-size: 20px;
    background-color: $darkBlue;
    color: $whiteBlue;
    animation: slideIn 0.5s cubic-bezier(0.075, 0.82, 0.165, 1) forwards;
    z-index: 999;

    p {
      padding: 0 5px 0 5px;
    }

    i  {
      padding: 5px;
      cursor: pointer;
    }
  }

  @keyframes slideIn {
    0% {
      transform: translateX(100%);
    }

    100% {
      transform: translateX(0%);
    }
    
  }
}

@media (max-width: 1680px) {

  $h1Size: 60px;

  section {
    padding: 60px;
  }

  .work {

    .projects li #hoverImg {
      left: 37%;
    }

    .cardtext {

      h2 {
        font-size: $h1Size;
      }

      p {
        font-size: 24px;
      }

      h4 {
        font-size: 20px;
      }
    }
  }

  .contacts {

    .cta {
      width: 40%;
    }

    .socials {
      justify-content: space-evenly;

      .github {
        margin: 0px 0 0px 0;
      }
    }

    form {

      input {
        margin-bottom: 15px;
      }

      .contactButton {
        margin-top: 0px;
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

    section {
      padding: 30px;
    }

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

  .work {

    .projects {

      .mainImage {
        margin: 0;
      }

      li {
        padding-bottom: 50px;
        margin-bottom: 50px;
        justify-content: center;
        flex-direction: column;

        #hoverImg,
        #hoverExpo {
          display: none;
        }

        .links {
          margin-bottom: 20px;
        }
      }
    }
  }

  .about {
    flex-direction: column;

    .aboutMe,
    .toolset {
      width: 100%;

      .title {
        border-top: 1px solid darken($color: $editorBlue, $amount: 10%);
      }
    }
  }

  .contacts {

    .content {
      flex-direction: column;

      .cta {
        width: 100%;

        video {
          width: 80%;
        }
      }
      
      .socials {
        width: 100%;
        flex-direction: row;
      }

      form {
        width: 100%;
      }
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

  .work .projects li { 

    .cardtext {
      width: 100%;
      h2 {
        font-size: 50px;
      }

      h3 {
        margin-bottom: 0;
      }

      h4 {
        display: none;
      }

      p {
        display: none;
      }

      .links {
        margin-top: 0;
        margin-bottom: 20px;
      }
    }
  }
}


@media (max-width: 600px) {

  section {
    padding-right: 40px;
    padding-left: 40px;
  }

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

  .work .projects li { 
    padding-bottom: 20px;
    margin-bottom: 0px;
    justify-content: center;

    .cardtext {
      width: 100%;
      h2 {
        font-size: 30px;
      }

    }
  }
}

@media (max-width: 450px) {


  .buttons .buttoes {
        display: flex;
        flex-direction: row;
        width: 100%;
      }

  .about .aboutMe {
    padding-bottom: 20px;
  }

  .about .toolset .editor .finalCode {
    margin-left: 10px;
  }

  .about .card .code p {
    font-size: 14px;
  }

  .about .card .editor .lineNumbers p{
    font-size: 14px;
  }

  .about .toolset .editor .finalCode p {
    font-size: 14px;
  }

  .about .toolset .editor .lineNumbers li {
    font-size: 14px;
  }

  .about .toolset .terminal .lastp {
    font-size: 14px;
    margin-left: 10px;
    word-break: break-all;
  }

   .about .toolset ul {
     justify-content: center;
   }

   .contacts {
     padding-bottom: 70px;
     padding-top: 70px;
     h1 {
       font-size: 36px;
      padding-left: 20px;
      padding-right: 20px;
     }

     h3 {
      margin: 0;
      padding-left: 20px;
      padding-right: 20px;
      font-weight: 300;
      font-size: 18px;
     }

     .content {
       padding: 20px;
     }
  }
   

  .contacts .content .socials {
    flex-wrap: wrap;
    justify-content: center;

    a {
      width: 50%;
    }

    .linkedInA {
      margin: 0;
    }

    .discord {
      margin-top: -100px
    }
  }
}

@media (max-width: 376px) {

    section {
      padding-right: 20px;
      padding-left: 20px;
    }
  .hero {
    flex-direction: column;
    padding-right: 20px;
    padding-left: 20px;
    padding-top: 100px;

    .heroText {
      width: 100%;

      h1 {
        flex-direction: column;
        font-size: 70px;
        margin-top: 10px;

        #firstName {
          margin-bottom: -30px;
        }
      }

      p {
        font-size: 16px;
      }
    }
  }

  .work .projects .seistetos {

    .cardtext h2 {
      line-height: 30px;
    }

    .link {
      
      .lastButton {
          margin-left: 10px;
        }
    }
  }

  .about .card .editor .blankSpace {
    margin-bottom: 10px;
  }
  
  
}

@media (max-width: 340px) {
   .about .card .code p {
    margin-left: 10px;
  }

  .about .aboutMe {
    padding-bottom: 0;
    margin-bottom: 10px;
  }

  .about .card {
    margin-bottom: 10px;
    padding-bottom: 0;
    z-index: 10;
  }
}
}
</style>