<template>
  <ScrollToTopButton v-if="!isAtTop" @click="scrollToElement('body')" />
  <li
    class="sun darkIcon"
    @click="toggleDarkMode()"
    v-if="!isDarkMode && mobileMode"
  >
    <a :style="{ color: darkBlue }"><i class="fas fa-sun"></i></a>
  </li>
  <li
    class="moon darkIcon"
    @click="toggleDarkMode()"
    v-else-if="isDarkMode && mobileMode"
  >
    <a :style="{ color: darkBlue }"><i class="fas fa-moon"></i></a>
  </li>
  <NavbarMobile
    v-if="mobileMode"
    :textColor="darkBlue"
    :backgroundColor="whiteBlue"
    @home="scrollToElement('body')"
    @work="scrollToElement('.work')"
    @about="scrollToElement('.about')"
    @contacts="scrollToElement('.contacts')"
  />
  <Navbar
    v-if="!mobileMode"
    class="navbar"
    @toggleTheme="toggleDarkMode()"
    :textColor="darkBlue"
    :isDarkMode="isDarkMode"
    @home="scrollToElement('body')"
    @work="scrollToElement('.work')"
    @about="scrollToElement('.about')"
    @contacts="scrollToElement('.contacts')"
  />
  <div
    v-if="!activatedNavbar"
    class="pageContent"
    :style="{ backgroundColor: whiteBlue, color: darkBlue }"
  >
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
    <section class="work">
      <ul class="projects">
        <li class="seistetos">
          <div class="cardtext" :style="{ opacity: opacityTeto }">
            <h2>
              <span :class="{ animate: isOnTeto }"
                >Grupo Académico Seistetos</span
              >
            </h2>
            <h3>
              <span :class="{ animate: isOnTeto }"
                >Front-end development and UX/UI Website Design</span
              >
            </h3>
            <p>
              <span :class="{ line1: isOnTeto }">
                <span :class="{ span1: isOnTeto }"
                  >A simple website redesign and
                </span>
              </span>
              <span :class="{ line1: isOnTeto }">
                <span :class="{ span2: isOnTeto }"
                  >development, bringing this</span
                >
              </span>
              <span :class="{ line1: isOnTeto }">
                <span :class="{ span3: isOnTeto }"
                  >university group's website up to</span
                >
              </span>
              <span :class="{ line1: isOnTeto }">
                <span :class="{ span4: isOnTeto }"
                  >date with a new and fresh layout.</span
                >
              </span>
            </p>
            <h4><span :class="{ animate: isOnTeto }">TechStack:</span></h4>
            <p class="tech">
              <span :class="{ animate: isOnTeto }"
                >HTML5, Sass, Vue.js, Vue Router, Typescript</span
              >
            </p>
            <div class="links">
              <div :class="{ link: isOnTeto }">
                <Button
                  buttonText="Live Website"
                  link="https://www.seistetos.uevora.pt/#/"
                  :style="{
                    backgroundColor: darkBlue,
                    color: whiteBlue,
                    borderColor: normalBlue,
                  }"
                />
                <Button
                  class="lastButton"
                  buttonText="Source Code"
                  link="https://github.com/MrValraven/seistetos"
                  :style="{
                    backgroundColor: whiteBlue,
                    color: darkBlue,
                    borderColor: darkBlue,
                  }"
                />
              </div>
            </div>
          </div>
          <img
            class="mainImage"
            src="@/assets/work/seistetos/seistetos.jpg"
            alt=""
          />
          <img
            class
            id="hoverImg"
            src="@/assets/work/seistetos/seistetosLogo.png"
            alt=""
          />
        </li>
        <li class="aaue">
          <div class="cardtext" :style="{ opacity: opacityAAUE }">
            <h2>
              <span :class="{ animate: isOnAAUE }">AAUE</span>
            </h2>
            <h3>
              <span :class="{ animate: isOnAAUE }">Fullstack Development</span>
            </h3>
            <p>
              <span :class="{ line1: isOnAAUE }">
                <span :class="{ span1: isOnAAUE }">Website da AAUE, </span>
              </span>
              <span :class="{ line1: isOnAAUE }">
                <span :class="{ span2: isOnAAUE }"
                  >Associação Académica responsável</span
                >
              </span>
              <span :class="{ line1: isOnAAUE }">
                <span :class="{ span3: isOnAAUE }"
                  >por potenciar o envolvimento e</span
                >
              </span>
              <span :class="{ line1: isOnAAUE }">
                <span :class="{ span4: isOnAAUE }"
                  >desenvolvimento académico dos alunos da UE</span
                >
              </span>
            </p>
            <h4><span :class="{ animate: isOnAAUE }">TechStack:</span></h4>
            <p class="tech">
              <span :class="{ animate: isOnAAUE }"
                >Vue.js, MongoDB, Express, JWT</span
              >
            </p>
            <div class="links">
              <div :class="{ link: isOnAAUE }">
                <Button
                  buttonText="Live Website"
                  link="https://aaue.pt/"
                  :style="{
                    backgroundColor: darkBlue,
                    color: whiteBlue,
                    borderColor: normalBlue,
                  }"
                />
                <Button
                  class="lastButton"
                  buttonText="Source Code"
                  link="https://github.com/MrValraven/aaue"
                  :style="{
                    backgroundColor: whiteBlue,
                    color: darkBlue,
                    borderColor: darkBlue,
                  }"
                />
              </div>
            </div>
          </div>
          <img
            class="mainImage"
            src="@/assets/work/aaue/aaueScreen.jpg"
            alt=""
          />
          <img class id="aaue" src="@/assets/work/aaue/aaue.svg" alt="" />
        </li>
        <li class="reitor">
          <div class="cardtext" :style="{ opacity: opacityReitor }">
            <h2>
              <span :class="{ animate: isOnReitor }">Desporto.aaue.pt</span>
            </h2>
            <h3>
              <span :class="{ animate: isOnReitor }"
                >Fullstack Development</span
              >
            </h3>
            <p>
              <span :class="{ line1: isOnReitor }">
                <span :class="{ span1: isOnReitor }">Website da secção </span>
              </span>
              <span :class="{ line1: isOnReitor }">
                <span :class="{ span2: isOnReitor }">desportiva da AAUE</span>
              </span>
              <span :class="{ line1: isOnReitor }">
                <span :class="{ span3: isOnReitor }"
                  >Responsável pelas diversas equipas da UE</span
                >
              </span>
              <span :class="{ line1: isOnReitor }">
                <span :class="{ span4: isOnReitor }"
                  >e pelo famoso Torneio do Reitor</span
                >
              </span>
            </p>
            <h4><span :class="{ animate: isOnReitor }">TechStack:</span></h4>
            <p class="tech">
              <span :class="{ animate: isOnReitor }"
                >React.js, SASS, React-Router-DOM
              </span>
            </p>
            <div class="links">
              <div :class="{ link: isOnReitor }">
                <Button
                  buttonText="Live Website"
                  link="https://desporto.aaue.pt/"
                  :style="{
                    backgroundColor: darkBlue,
                    color: whiteBlue,
                    borderColor: normalBlue,
                  }"
                />
                <Button
                  class="lastButton"
                  buttonText="Source Code"
                  link="https://github.com/MrValraven/torneioreitor"
                  :style="{
                    backgroundColor: whiteBlue,
                    color: darkBlue,
                    borderColor: darkBlue,
                  }"
                />
              </div>
            </div>
          </div>
          <img class="mainImage" src="@/assets/work/reitor/reitor.jpg" alt="" />
          <img class id="aaue" src="@/assets/work/reitor/football.svg" alt="" />
        </li>
        <li class="kucomcu">
          <div class="cardtext" :style="{ opacity: opacityKucomcu }">
            <h2>
              <span :class="{ animate: isOnKucomcu }">Kucomcu.io</span>
            </h2>
            <h3>
              <span :class="{ animate: isOnKucomcu }"
                >Fullstack Development</span
              >
            </h3>
            <p>
              <span :class="{ line1: isOnKucomcu }">
                <span :class="{ span1: isOnKucomcu }"
                  >Welcome to the cryptoverse!
                </span>
              </span>
              <span :class="{ line1: isOnKucomcu }">
                <span :class="{ span2: isOnKucomcu }">
                  Visit Kucomcu.io to send</span
                >
              </span>
              <span :class="{ line1: isOnKucomcu }">
                <span :class="{ span3: isOnKucomcu }">ETH to your peers!</span>
              </span>
              <span :class="{ line1: isOnKucomcu }">
                <span :class="{ span4: isOnKucomcu }">
                  Now live on the Ropsen Testnet</span
                >
              </span>
            </p>
            <h4><span :class="{ animate: isOnKucomcu }">TechStack:</span></h4>
            <p class="tech">
              <span :class="{ animate: isOnKucomcu }"
                >React, Hooks, ContextAPI, TailwindCSS, Solidity</span
              >
            </p>
            <div class="links">
              <div :class="{ link: isOnKucomcu }">
                <Button
                  buttonText="Live Website"
                  link="https://kucomcu-io.vercel.app/"
                  :style="{
                    backgroundColor: darkBlue,
                    color: whiteBlue,
                    borderColor: normalBlue,
                  }"
                />
                <Button
                  class="lastButton"
                  buttonText="Source Code"
                  link="https://github.com/MrValraven/kucomcu.io"
                  :style="{
                    backgroundColor: whiteBlue,
                    color: darkBlue,
                    borderColor: darkBlue,
                  }"
                />
              </div>
            </div>
          </div>
          <img
            class="mainImage"
            src="@/assets/work/kucomcu/kucomcu.jpg"
            alt=""
          />
          <img class id="eth" src="@/assets/work/kucomcu/ethereum.svg" alt="" />
        </li>
        <li class="expoestudante">
          <div class="cardtext" :style="{ opacity: opacityExpo }">
            <h2><span :class="{ animate: isOnExpo }">Expo Estudante</span></h2>
            <h3>
              <span :class="{ animate: isOnExpo }">Fullstack development</span>
            </h3>
            <p>
              <span :class="{ line1: isOnExpo }">
                <span :class="{ span1: isOnExpo }"
                  >A modern approach to the
                </span>
              </span>
              <span :class="{ line1: isOnExpo }">
                <span :class="{ span2: isOnExpo }">
                  upcoming technology and
                </span>
              </span>
              <span :class="{ line1: isOnExpo }">
                <span :class="{ span3: isOnExpo }">
                  student oriented event in
                </span>
              </span>
              <span :class="{ line1: isOnExpo }">
                <span :class="{ span4: isOnExpo }"> Évora, Portugal.</span>
              </span>
            </p>
            <h4><span :class="{ animate: isOnExpo }">TechStack:</span></h4>
            <p class="tech">
              <span :class="{ animate: isOnExpo }"
                >HTML5, Sass, Vue.js, Node.js, Typescript</span
              >
            </p>
            <div class="links">
              <div :class="{ link: isOnExpo }">
                <Button
                  buttonText="Live Website"
                  link="https://expoestudante.aaue.pt/#/"
                  :style="{
                    backgroundColor: darkBlue,
                    color: whiteBlue,
                    borderColor: normalBlue,
                  }"
                />
              </div>
            </div>
          </div>
          <img
            class="mainImage"
            src="@/assets/work/expoestudante/expoestudante.jpg"
            alt=""
          />
          <img
            class
            id="hoverExpo"
            src="@/assets/work/expoestudante/logo.png"
            alt=""
          />
        </li>
      </ul>
    </section>
    <section class="sideprojects">
      <h1>Side Projects</h1>
      <div class="container">
        <SideProject
          v-for="(sideproject, index) in sideprojects.slice(
            0,
            currentSideprojectsLength
          )"
          :key="index"
          :title="sideproject.title"
          :description="sideproject.description"
          :websiteURL="sideproject.websiteURL"
          :codeURL="sideproject.codeURL"
          :styles="{
            backgroundColor: darkBlue,
            color: whiteBlue,
            borderColor: normalBlue,
          }"
        />
      </div>
      <Button
        class="showMoreButton"
        @click="showAllProjects"
        v-if="currentSideprojectsLength !== sideprojects.length"
        style="width: 30%; margin-top: 50px"
        buttonText="Show more +"
      />
    </section>
    <section class="about">
      <div class="aboutMe">
        <div class="card">
          <h1 class="title">Home.vue - portefolio - Visual Studio Code</h1>
          <h1 class="file">
            <span>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 48 48"
                width="20px"
                height="20px"
              >
                <polygon
                  fill="#81c784"
                  points="23.987,17 18.734,8 2.974,8 23.987,44 45,8 29.24,8"
                />
                <polygon
                  fill="#455a64"
                  points="29.24,8 23.987,17 18.734,8 11.146,8 23.987,30 36.828,8"
                />
              </svg>
              Home.vue
              <i class="fas fa-times"></i>
            </span>
          </h1>
          <h2>
            src
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
                <span id="me" class="code-red"></span>
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
                <span id="idade" class="code-green"></span>
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
                <span class="code-green"
                  ><a
                    href="https://github.com/MrValraven"
                    target="_blank"
                    id="githubLink"
                    class="code-green"
                    rel="noopener noreferrer"
                  ></a
                ></span>
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
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 48 48"
              width="20px"
              height="20px"
            >
              <rect width="36" height="36" x="6" y="6" fill="#1976d2" />
              <polygon
                fill="#fff"
                points="27.49,22 14.227,22 14.227,25.264 18.984,25.264 18.984,40 22.753,40 22.753,25.264 27.49,25.264"
              />
              <path
                fill="#fff"
                d="M39.194,26.084c0,0-1.787-1.192-3.807-1.192s-2.747,0.96-2.747,1.986 c0,2.648,7.381,2.383,7.381,7.712c0,8.209-11.254,4.568-11.254,4.568V35.22c0,0,2.152,1.622,4.733,1.622s2.483-1.688,2.483-1.92 c0-2.449-7.315-2.449-7.315-7.878c0-7.381,10.658-4.469,10.658-4.469L39.194,26.084z"
              />
            </svg>
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
        <div :class="{ terminalOn: codeEnd }" class="terminal">
          <p :class="{ terminalOnOptions: codeEnd }" class="terminalOptions">
            Problems Output Debug Console <span>Terminal</span>
          </p>
          <p class="toolCode lastp"></p>
        </div>

        <ul>
          <li :class="{ html: codeEnd }">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
              <path
                d="M21.963,11.481l-9.457-0.008l0.224,2.531l9.006,0.007l-0.684,7.587l-5.066,1.4L15.981,23l-5.061-1.409l-0.351-3.968l2.481,0.002l0.182,2.059l2.752,0.746l0.003-0.001v0l2.756-0.741l0.289-3.205l-3.042-0.002l-5.523-0.004L9.807,9l6.19,0.005l6.19,0.005L21.963,11.481z"
              />
              <path
                fill="none"
                stroke="#ffffff"
                stroke-miterlimit="10"
                stroke-width="2"
                d="M6.309,5l1.749,19.795L15.977,27l7.93-2.191l1.783-19.793L6.309,5z"
              />
            </svg>
            <p>HTML5</p>
          </li>
          <li :class="{ css: codeEnd }">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
              <path
                d="M6,4l2,21l8,3l8-3l2-21H6z M22.391,10l-5.696,3h2.427H22h0.123l-0.512,6.007L21.631,19l-0.275,3L16,24l-5.366-2l-0.329-4 h3.021l0.157,2.034L16,20.904l2.521-0.853L18.867,16H10.13l-0.257-3l5.91-3H9.609L9.332,7h13.32L22.391,10z"
              />
            </svg>
            <p>CSS3</p>
          </li>
          <li :class="{ sass: codeEnd }">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
              <path
                d="M27.534,17.792c-1.118,0.006-2.086,0.274-2.898,0.674c-0.297-0.592-0.597-1.114-0.648-1.501	c-0.059-0.452-0.127-0.722-0.056-1.261c0.071-0.539,0.383-1.302,0.378-1.359c-0.005-0.057-0.07-0.332-0.715-0.336	c-0.645-0.005-1.196,0.124-1.261,0.294c-0.065,0.17-0.189,0.553-0.266,0.953c-0.113,0.585-1.287,2.67-1.954,3.761	c-0.218-0.426-0.403-0.801-0.442-1.098c-0.059-0.452-0.127-0.722-0.056-1.261c0.071-0.539,0.383-1.302,0.378-1.359	c-0.005-0.057-0.07-0.332-0.715-0.336c-0.645-0.005-1.196,0.124-1.261,0.294c-0.065,0.17-0.134,0.568-0.266,0.953	c-0.132,0.385-1.693,3.863-2.102,4.765c-0.208,0.459-0.39,0.828-0.518,1.08c0-0.001-0.001-0.001-0.001-0.001	s-0.008,0.017-0.021,0.045c-0.11,0.215-0.175,0.333-0.175,0.333s0.001,0.002,0.002,0.004c-0.087,0.158-0.18,0.304-0.226,0.304	c-0.032,0-0.097-0.419,0.014-0.995c0.232-1.207,0.79-3.088,0.785-3.153c-0.003-0.033,0.104-0.361-0.364-0.533	c-0.455-0.167-0.617,0.111-0.659,0.112c-0.04,0.001-0.07,0.098-0.07,0.098s0.507-2.116-0.967-2.116	c-0.921,0-2.198,1.008-2.827,1.922c-0.397,0.217-1.246,0.68-2.148,1.175c-0.346,0.19-0.699,0.384-1.034,0.569	c-0.023-0.025-0.045-0.05-0.069-0.075c-1.787-1.907-5.091-3.255-4.951-5.819c0.051-0.932,0.375-3.386,6.348-6.362	c4.893-2.438,8.81-1.767,9.487-0.28c0.967,2.124-2.094,6.073-7.175,6.642c-1.936,0.217-2.955-0.533-3.209-0.813	c-0.267-0.294-0.307-0.307-0.406-0.252c-0.162,0.09-0.059,0.35,0,0.504c0.152,0.395,0.774,1.095,1.836,1.443	c0.934,0.306,3.207,0.475,5.956-0.589c3.079-1.191,5.483-4.504,4.777-7.273c-0.718-2.816-5.388-3.742-9.808-2.172	C7.597,5.708,4.749,7.175,2.702,9.09c-2.434,2.277-2.823,4.259-2.663,5.087c0.568,2.942,4.624,4.858,6.248,6.278	c-0.08,0.044-0.155,0.086-0.224,0.123c-0.814,0.403-3.905,2.021-4.679,3.73c-0.877,1.939,0.14,3.33,0.813,3.517	c2.086,0.58,4.226-0.464,5.376-2.179c1.15-1.715,1.009-3.948,0.482-4.968c-0.007-0.013-0.014-0.025-0.021-0.038	c0.21-0.124,0.425-0.251,0.637-0.376c0.414-0.243,0.821-0.47,1.174-0.662c-0.197,0.541-0.342,1.19-0.417,2.127	c-0.088,1.101,0.363,2.523,0.953,3.083c0.26,0.246,0.573,0.252,0.771,0.252c0.687,0,1-0.571,1.345-1.247	c0.423-0.829,0.799-1.794,0.799-1.794s-0.471,2.606,0.813,2.606c0.468,0,0.939-0.607,1.148-0.916	c0.001,0.003,0.001,0.005,0.001,0.005s0.012-0.02,0.036-0.061c0.049-0.074,0.076-0.122,0.076-0.122s0.001-0.005,0.002-0.013	c0.188-0.327,0.605-1.071,1.231-2.299c0.808-1.586,1.583-3.573,1.583-3.573s0.072,0.486,0.308,1.289	c0.139,0.473,0.434,0.995,0.667,1.496c-0.187,0.26-0.303,0.41-0.303,0.41s0.001,0.003,0.003,0.008	c-0.15,0.199-0.318,0.414-0.494,0.623c-0.638,0.76-1.398,1.627-1.499,1.878c-0.12,0.295-0.092,0.512,0.14,0.687	c0.169,0.128,0.47,0.147,0.785,0.126c0.573-0.039,0.977-0.181,1.176-0.267c0.31-0.11,0.671-0.282,1.011-0.531	c0.626-0.46,1.003-1.118,0.967-1.99c-0.02-0.48-0.173-0.957-0.367-1.406c0.057-0.082,0.114-0.164,0.171-0.247	c0.987-1.442,1.752-3.027,1.752-3.027s0.072,0.486,0.308,1.289c0.12,0.407,0.355,0.85,0.567,1.285	c-0.928,0.754-1.503,1.629-1.703,2.204c-0.369,1.063-0.08,1.544,0.462,1.654c0.246,0.05,0.593-0.063,0.854-0.173	c0.325-0.108,0.715-0.287,1.08-0.555c0.626-0.46,1.227-1.104,1.191-1.976c-0.017-0.397-0.124-0.791-0.27-1.169	c0.786-0.328,1.804-0.51,3.101-0.358c2.782,0.325,3.327,2.062,3.223,2.789c-0.104,0.727-0.688,1.127-0.883,1.247	c-0.195,0.121-0.255,0.163-0.238,0.252c0.024,0.13,0.114,0.125,0.28,0.097c0.229-0.039,1.461-0.591,1.513-1.933	C32.057,19.648,30.425,17.777,27.534,17.792z M6.093,25.021c-0.921,1.005-2.209,1.385-2.761,1.065	c-0.596-0.346-0.36-1.825,0.771-2.892c0.689-0.65,1.579-1.249,2.169-1.618c0.134-0.081,0.332-0.2,0.571-0.343	c0.04-0.023,0.062-0.035,0.062-0.035l-0.001-0.001c0.046-0.028,0.094-0.056,0.143-0.085C7.459,22.629,7.06,23.966,6.093,25.021z M12.805,20.457c-0.321,0.782-0.993,2.784-1.401,2.677c-0.351-0.092-0.565-1.614-0.07-3.111c0.249-0.754,0.781-1.654,1.093-2.004	c0.503-0.563,1.057-0.747,1.191-0.518C13.789,17.791,13.006,19.967,12.805,20.457z M18.351,23.103	c-0.136,0.071-0.261,0.116-0.319,0.081c-0.043-0.025,0.056-0.119,0.056-0.119s0.694-0.746,0.967-1.086	c0.159-0.198,0.343-0.432,0.544-0.695c0.002,0.026,0.003,0.052,0.003,0.078C19.599,22.257,18.736,22.861,18.351,23.103z M22.623,22.13c-0.101-0.072-0.085-0.306,0.249-1.033c0.131-0.286,0.43-0.766,0.95-1.225c0.06,0.189,0.097,0.37,0.096,0.539	C23.911,21.535,23.108,21.955,22.623,22.13z"
              />
            </svg>
            <p>SASS</p>
          </li>
          <li :class="{ js: codeEnd }">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
              <path
                d="M23,20.767C23,22.211,21.86,23,20.34,23c-1.492,0-2.461-0.713-2.926-1.644l1.311-0.751 c0.342,0.561,0.789,0.979,1.577,0.979c0.665,0,1.093-0.333,1.093-0.798c0-0.551-0.437-0.741-1.169-1.064l-0.399-0.171 c-1.159-0.494-1.929-1.121-1.929-2.432c0-1.207,0.922-2.119,2.347-2.119c1.026,0,1.758,0.352,2.29,1.283L21.28,17.09 c-0.276-0.494-0.57-0.694-1.036-0.694c-0.475,0-0.77,0.304-0.77,0.694c0,0.475,0.295,0.675,0.988,0.979l0.399,0.171 C22.23,18.819,23,19.418,23,20.767z"
              />
              <path
                d="M16,15.095v5.482C16,22.24,15.021,23,13.596,23c-1.283,0-2.033-0.665-2.413-1.473l1.311-0.789 c0.247,0.447,0.485,0.827,1.036,0.827c0.523,0,0.865-0.209,0.865-1.007v-5.463H16z"
              />
              <path d="M5,5v22h22V5H5z M7,7h18v18H7V7z" />
            </svg>
            <p>Javascript</p>
          </li>
          <li :class="{ ts: codeEnd }">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
              <rect
                width="22"
                height="22"
                x="5"
                y="5"
                fill="none"
                stroke="#ffffff"
                stroke-miterlimit="10"
                stroke-width="2"
              />
              <polygon
                points="17.588,14 10.325,14 10.325,15.873 12.879,15.873 12.879,24.016 14.98,24.016 14.98,15.873 17.588,15.873"
              />
              <path
                d="M23.547,16.373c0,0-0.978-0.652-2.083-0.652c-1.105,0-1.503,0.525-1.503,1.087c0,1.449,4.039,1.304,4.039,4.22	c0,4.492-6.158,2.5-6.158,2.5v-2.155c0,0,1.177,0.888,2.59,0.888s1.358-0.924,1.358-1.051c0-1.34-4.003-1.34-4.003-4.311	c0-4.039,5.832-2.445,5.832-2.445L23.547,16.373z"
              />
            </svg>
            <p>Typescript</p>
          </li>
          <li :class="{ vue: codeEnd }">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
              <path
                d="M25.5,8L16,24.1L6.5,8h5.3l2.4,4.2l1.7,3l1.7-3L20.2,8H25.5 M29,6H19l-3,5.3L13,6H3l13,22L29,6L29,6z"
              />
              <polygon points="19.6,7 16,12 12.4,7 9.7,7 16,18 22.3,7" />
              <polygon points="19.6,7 16,12 12.4,7 9.7,7 16,18 22.3,7" />
            </svg>
            <p>Vue.js</p>
          </li>
          <li :class="{ node: codeEnd }">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
              <path
                d="M26.96,9l-9.92-5.73c-0.63-0.36-1.46-0.36-2.09,0L5.04,8.99C4.4,9.36,4,10.06,4,10.8v10.38c0,0.75,0.4,1.44,1.04,1.81 l2.6,1.5c1.26,0.62,1.71,0.62,2.28,0.62c1.87,0,2.94-1.13,2.94-3.09V11.31c0-0.16-0.13-0.29-0.29-0.29h-1.25 c-0.17,0-0.29,0.13-0.29,0.29v10.7c0,0.88-0.91,1.74-2.38,1.01l-2.72-1.57c-0.1-0.05-0.16-0.16-0.16-0.27V10.81 c0-0.12,0.06-0.22,0.16-0.28l9.91-5.72c0.09-0.06,0.21-0.06,0.31,0l9.91,5.72c0.1,0.06,0.16,0.16,0.16,0.27v10.38 c0,0.11-0.06,0.22-0.15,0.27l-9.92,5.73c-0.09,0.05-0.22,0.05-0.31,0l-2.55-1.51c-0.07-0.05-0.17-0.06-0.24-0.02 c-0.71,0.4-0.84,0.45-1.5,0.68c-0.16,0.05-0.41,0.15,0.09,0.43l3.31,1.96C15.27,28.9,15.63,29,15.99,29c0.37,0,0.73-0.1,1.05-0.28 l9.92-5.73C27.6,22.62,28,21.93,28,21.18V10.81C28,10.06,27.6,9.37,26.96,9z"
              />
              <path
                d="M24,18.595c0,2.16-1.8,3.4-4.94,3.4c-4.34,0-5.25-1.99-5.25-3.66c0-0.15,0.12-0.28,0.28-0.28h1.29 c0.14,0,0.26,0.1,0.28,0.24c0.19,1.3,0.77,1.96,3.4,1.96c2.09,0,2.98-0.47,2.98-1.57c0-0.64-0.25-1.12-3.5-1.44 c-2.72-0.27-4.4-0.87-4.4-3.04c0-2,1.69-3.2,4.52-3.2c3.18,0,4.75,1.11,4.95,3.47c0.01,0.09-0.02,0.17-0.07,0.22 c-0.06,0.06-0.13,0.1-0.21,0.1h-1.29c-0.14,0-0.25-0.1-0.28-0.23c-0.31-1.37-1.07-1.81-3.1-1.81c-2.28,0-2.55,0.79-2.55,1.39 c0,0.72,0.31,0.93,3.4,1.33C22.55,15.885,24,16.455,24,18.595z"
              />
            </svg>
            <p>Node.js</p>
          </li>
          <li :class="{ npm: codeEnd }">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 32 32"
              width="64"
              height="64"
            >
              <path
                d="M32 24.795c-1.164.296-1.884.013-2.53-.957l-4.594-6.356-.664-.88-5.365 7.257c-.613.873-1.256 1.253-2.4.944l6.87-9.222-6.396-8.33c1.1-.214 1.86-.105 2.535.88l4.765 6.435 4.8-6.4c.615-.873 1.276-1.205 2.38-.883l-2.48 3.288-3.36 4.375c-.4.5-.345.842.023 1.325L32 24.795zM.008 15.427l.562-2.764C2.1 7.193 8.37 4.92 12.694 8.3c2.527 1.988 3.155 4.8 3.03 7.95H1.48c-.214 5.67 3.867 9.092 9.07 7.346 1.825-.613 2.9-2.042 3.438-3.83.273-.896.725-1.036 1.567-.78-.43 2.236-1.4 4.104-3.45 5.273-3.063 1.75-7.435 1.184-9.735-1.248C1 21.6.434 19.812.18 17.9c-.04-.316-.12-.617-.18-.92q.008-.776.008-1.552zm1.498-.38h12.872c-.084-4.1-2.637-7.012-6.126-7.037-3.83-.03-6.58 2.813-6.746 7.037z"
              />
            </svg>
            <p>Express.js</p>
          </li>
          <li :class="{ yarn: codeEnd }">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 50 50">
              <path
                :fill="editorBlue"
                d="M42,17.3C42,37.8,24,44,24,44S6,37.8,6,17.3c0-2.5,0.2-4.6,0.4-6.3c0.3-2.5,2-4.5,4.4-5.1 C13.9,5,18.8,4,24,4s10.1,1,13.3,1.9c2.4,0.6,4.1,2.7,4.4,5.1C41.8,12.7,42,14.9,42,17.3z"
              />
              <path
                fill="#ffffff"
                d="M24,7c4.9,0,9.5,1,12.5,1.8c1.2,0.3,2,1.3,2.2,2.6c0.2,1.9,0.3,3.9,0.3,5.9c0,15.6-11.5,21.9-15,23.4 c-3.5-1.6-15-7.9-15-23.4c0-2,0.1-4,0.3-5.9c0.1-1.3,1-2.3,2.2-2.6C14.5,8,19.1,7,24,7 M24,4c-5.2,0-10.1,1-13.3,1.9 C8.4,6.5,6.6,8.6,6.4,11C6.2,12.7,6,14.9,6,17.3C6,37.8,24,44,24,44s18-6.2,18-26.7c0-2.5-0.2-4.6-0.4-6.3c-0.3-2.5-2-4.5-4.4-5.1 C34.1,5,29.2,4,24,4L24,4z"
              />
              <path fill="#dcedc8" d="M23 28H25V36H23z" />
              <path
                fill="#ffffff"
                d="M24,10c0,0-6,5-6,13c0,5.2,3.3,8.5,5,10l1-3l1,3c1.7-1.5,5-4.8,5-10C30,15,24,10,24,10z"
              />
              <path
                fill="#d1d1d1"
                d="M24,10c0,0-6,5-6,13c0,5.2,3.3,8.5,5,10l1-3V10z"
              />
            </svg>
            <p>MongoDB</p>
          </li>
          <li :class="{ gitalt: codeEnd }">
            <i class="fab fa-git-alt"></i>
            <p>Git</p>
          </li>
          <li :class="{ sql: codeEnd }">
            <svg viewBox="0 0 32 32" xmlns="http://www.w3.org/2000/svg">
              <path
                d="M 11.404297 3.359375 C 10.558989 3.3033199 9.7282187 3.4545628 9 3.875 C 8.0290418 4.435583 7.3824561 5.3924554 7.0351562 6.4941406 C 6.6878566 7.5958258 6.6075884 8.8654625 6.734375 10.251953 C 6.7472175 10.392393 6.7719235 10.538778 6.7890625 10.681641 C 6.6565239 10.738327 6.516949 10.790405 6.3886719 10.849609 C 5.1245423 11.433054 4.0655937 12.136668 3.2851562 12.988281 C 2.5047189 13.839894 2 14.878834 2 16 C 2 17.121166 2.5047188 18.160106 3.2851562 19.011719 C 4.0655937 19.863332 5.1245423 20.566946 6.3886719 21.150391 C 6.516949 21.209595 6.6565239 21.261673 6.7890625 21.318359 C 6.7719235 21.461222 6.7472175 21.607607 6.734375 21.748047 C 6.6075884 23.134538 6.6878566 24.404174 7.0351562 25.505859 C 7.3824561 26.607544 8.0290418 27.564417 9 28.125 C 9.9709582 28.685583 11.122263 28.76765 12.25 28.517578 C 13.377738 28.267506 14.516954 27.701483 15.654297 26.898438 C 15.769442 26.817137 15.884905 26.722947 16 26.636719 C 16.115095 26.722947 16.230558 26.817137 16.345703 26.898438 C 17.483046 27.701483 18.622262 28.267506 19.75 28.517578 C 20.877737 28.76765 22.029042 28.685583 23 28.125 C 23.970958 27.564417 24.617544 26.607544 24.964844 25.505859 C 25.312144 24.404174 25.392412 23.134538 25.265625 21.748047 C 25.252783 21.607607 25.228076 21.461222 25.210938 21.318359 C 25.343476 21.261673 25.483051 21.209595 25.611328 21.150391 C 26.875458 20.566946 27.934406 19.863332 28.714844 19.011719 C 29.495281 18.160106 30 17.121166 30 16 C 30 14.878834 29.495281 13.839894 28.714844 12.988281 C 27.934406 12.136668 26.875458 11.433054 25.611328 10.849609 C 25.483051 10.790405 25.343476 10.738327 25.210938 10.681641 C 25.228076 10.538778 25.252783 10.392393 25.265625 10.251953 C 25.392412 8.8654622 25.312144 7.5958262 24.964844 6.4941406 C 24.617544 5.3924558 23.970958 4.435583 23 3.875 C 22.029042 3.314417 20.877737 3.2323501 19.75 3.4824219 C 18.622262 3.7324945 17.483046 4.2985163 16.345703 5.1015625 C 16.230558 5.1828631 16.115095 5.2770534 16 5.3632812 C 15.884905 5.2770534 15.769442 5.1828632 15.654297 5.1015625 C 14.516954 4.2985167 13.377738 3.7324941 12.25 3.4824219 C 11.968066 3.4199038 11.686066 3.37806 11.404297 3.359375 z M 11.273438 5.3515625 C 11.44385 5.3643925 11.625005 5.3926711 11.818359 5.4355469 C 12.574044 5.6031175 13.479049 6.027269 14.433594 6.6914062 C 13.638579 7.445577 12.856199 8.3035536 12.109375 9.2636719 C 10.905846 9.4303655 9.7722189 9.6771858 8.7226562 9.9882812 C 8.6249172 8.8300209 8.708758 7.8336973 8.9414062 7.0957031 C 9.1795887 6.3401532 9.5360797 5.8752664 10 5.6074219 C 10.34794 5.4065385 10.762201 5.3130725 11.273438 5.3515625 z M 20.726562 5.3515625 C 21.237799 5.3130724 21.65206 5.4065385 22 5.6074219 C 22.46392 5.8752664 22.820412 6.3401534 23.058594 7.0957031 C 23.291242 7.8336973 23.375082 8.830021 23.277344 9.9882812 C 22.227781 9.6771858 21.094154 9.4303655 19.890625 9.2636719 C 19.143801 8.3035536 18.361421 7.445577 17.566406 6.6914062 C 18.520951 6.0272696 19.425956 5.6031175 20.181641 5.4355469 C 20.374995 5.3926712 20.556151 5.3643925 20.726562 5.3515625 z M 16 7.9589844 C 16.351492 8.2839608 16.702356 8.645337 17.052734 9.0234375 C 16.704015 9.0111056 16.355492 9 16 9 C 15.644508 9 15.295985 9.0111056 14.947266 9.0234375 C 15.297644 8.645337 15.648508 8.2839609 16 7.9589844 z M 16 11 C 16.964537 11 17.899388 11.05672 18.798828 11.152344 C 19.331359 11.883468 19.847811 12.66469 20.330078 13.5 C 20.81238 14.335371 21.230731 15.173194 21.597656 16 C 21.230731 16.826806 20.81238 17.664629 20.330078 18.5 C 19.847811 19.33531 19.331359 20.116532 18.798828 20.847656 C 17.899388 20.94328 16.964537 21 16 21 C 15.035463 21 14.100612 20.94328 13.201172 20.847656 C 12.668641 20.116532 12.152189 19.33531 11.669922 18.5 C 11.18762 17.664629 10.769268 16.826806 10.402344 16 C 10.769268 15.173194 11.18762 14.335371 11.669922 13.5 C 12.152189 12.66469 12.668641 11.883468 13.201172 11.152344 C 14.100612 11.05672 15.035463 11 16 11 z M 10.484375 11.599609 C 10.299345 11.895429 10.115237 12.192151 9.9375 12.5 C 9.7597627 12.80785 9.5953134 13.115677 9.4316406 13.423828 C 9.2796229 12.932067 9.1426994 12.44671 9.0371094 11.980469 C 9.4941217 11.838603 9.981943 11.71397 10.484375 11.599609 z M 21.515625 11.599609 C 22.018057 11.71397 22.505878 11.838603 22.962891 11.980469 C 22.857301 12.44671 22.720377 12.932067 22.568359 13.423828 C 22.404687 13.115677 22.240237 12.80785 22.0625 12.5 C 21.884763 12.192151 21.700655 11.895429 21.515625 11.599609 z M 7.1542969 12.703125 C 7.409859 13.768497 7.7627696 14.873405 8.2207031 16 C 7.7627696 17.126595 7.409859 18.231503 7.1542969 19.296875 C 6.1028081 18.802492 5.282404 18.230459 4.7597656 17.660156 C 4.2245315 17.076109 4 16.535689 4 16 C 4 15.464311 4.2245315 14.923891 4.7597656 14.339844 C 5.282404 13.769541 6.1028081 13.197508 7.1542969 12.703125 z M 24.845703 12.703125 C 25.897191 13.197508 26.717596 13.769541 27.240234 14.339844 C 27.775468 14.923891 28 15.464311 28 16 C 28 16.535689 27.775468 17.076109 27.240234 17.660156 C 26.717596 18.230459 25.897191 18.802492 24.845703 19.296875 C 24.590141 18.231503 24.23723 17.126595 23.779297 16 C 24.23723 14.873405 24.590141 13.768497 24.845703 12.703125 z M 16 13 C 14.35499 13 13 14.35499 13 16 C 13 17.64501 14.35499 19 16 19 C 17.64501 19 19 17.64501 19 16 C 19 14.35499 17.64501 13 16 13 z M 16 15 C 16.564129 15 17 15.435871 17 16 C 17 16.564129 16.564129 17 16 17 C 15.435871 17 15 16.564129 15 16 C 15 15.435871 15.435871 15 16 15 z M 9.4316406 18.576172 C 9.5953134 18.884323 9.7597627 19.19215 9.9375 19.5 C 10.115237 19.807849 10.299345 20.104571 10.484375 20.400391 C 9.981943 20.28603 9.4941217 20.161397 9.0371094 20.019531 C 9.1426994 19.55329 9.2796229 19.067933 9.4316406 18.576172 z M 22.568359 18.576172 C 22.720377 19.067933 22.857301 19.55329 22.962891 20.019531 C 22.505878 20.161397 22.018057 20.28603 21.515625 20.400391 C 21.700655 20.104571 21.884763 19.807849 22.0625 19.5 C 22.240237 19.19215 22.404687 18.884323 22.568359 18.576172 z M 8.7226562 22.011719 C 9.7722189 22.322814 10.905846 22.569634 12.109375 22.736328 C 12.856199 23.696446 13.638579 24.554423 14.433594 25.308594 C 13.479049 25.97273 12.574044 26.396882 11.818359 26.564453 C 11.044942 26.735955 10.46392 26.660422 10 26.392578 C 9.5360797 26.124733 9.1795888 25.659846 8.9414062 24.904297 C 8.708758 24.166302 8.6249172 23.169979 8.7226562 22.011719 z M 23.277344 22.011719 C 23.375082 23.169979 23.29124 24.166302 23.058594 24.904297 C 22.820412 25.659847 22.46392 26.124733 22 26.392578 C 21.53608 26.660422 20.955057 26.735956 20.181641 26.564453 C 19.425956 26.396882 18.520951 25.97273 17.566406 25.308594 C 18.361421 24.554423 19.143801 23.696446 19.890625 22.736328 C 21.094154 22.569634 22.227781 22.322814 23.277344 22.011719 z M 14.947266 22.976562 C 15.295985 22.988894 15.644508 23 16 23 C 16.355492 23 16.704015 22.988894 17.052734 22.976562 C 16.702356 23.354663 16.351492 23.716039 16 24.041016 C 15.648508 23.716039 15.297644 23.354663 14.947266 22.976562 z"
              />
            </svg>
            <p>React.js</p>
          </li>
          <li :class="{ redux: codeEnd }">
            <svg
              viewBox="0 0 24 24"
              role="img"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M16.633 16.504c.869-.075 1.543-.84 1.499-1.754-.046-.914-.795-1.648-1.708-1.648h-.061c-.943.031-1.678.824-1.648 1.769.03.479.226.869.494 1.153-1.048 2.038-2.621 3.536-5.004 4.795-1.603.838-3.296 1.154-4.944.929-1.378-.194-2.456-.81-3.116-1.798-.988-1.499-1.078-3.116-.255-4.734.601-1.169 1.499-2.023 2.099-2.443-.15-.389-.33-1.048-.42-1.542-4.436 3.177-3.985 7.521-2.637 9.574 1.004 1.498 3.057 2.456 5.304 2.456.599 0 1.229-.044 1.843-.194 3.896-.749 6.847-3.086 8.54-6.532l.014-.031zM21.981 12.758c-2.321-2.727-5.738-4.225-9.634-4.225h-.51c-.253-.554-.837-.899-1.497-.899h-.045c-.943 0-1.678.81-1.647 1.753.03.898.794 1.648 1.708 1.648h.074c.675-.03 1.259-.45 1.498-1.049h.555c2.309 0 4.495.674 6.488 1.992 1.527 1.004 2.622 2.322 3.236 3.896.538 1.288.509 2.547-.045 3.597-.854 1.647-2.293 2.517-4.195 2.517-1.199 0-2.367-.375-2.967-.644-.359.298-.959.793-1.394 1.093 1.318.598 2.652.943 3.94.943 2.922 0 5.093-1.647 5.918-3.236.898-1.798.824-4.824-1.469-7.416l-.014.03zM6.49 17.042c.029.899.793 1.648 1.708 1.648h.06c.959-.03 1.693-.823 1.648-1.768 0-.899-.779-1.647-1.693-1.647h-.061c-.06 0-.149 0-.225.029-1.243-2.098-1.768-4.346-1.572-6.771.119-1.828.719-3.417 1.797-4.735.899-1.124 2.592-1.679 3.746-1.708 3.236-.061 4.585 3.971 4.689 5.574l1.498.449c-.345-4.914-3.4-7.492-6.322-7.492-2.742 0-5.273 1.993-6.293 4.915-1.393 3.896-.479 7.641 1.229 10.638-.149.195-.239.539-.209.868z"
              />
            </svg>
            <p>Redux</p>
          </li>
          <li :class="{ nextjs: codeEnd }">
            <svg
              viewBox="0 0 15 15"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M4.5 4.5L4.90534 4.20725C4.77836 4.03144 4.55252 3.95753 4.34617 4.02425C4.13981 4.09098 4 4.28313 4 4.5H4.5ZM7.5 14C3.91015 14 1 11.0899 1 7.5H0C0 11.6421 3.35786 15 7.5 15V14ZM14 7.5C14 11.0899 11.0899 14 7.5 14V15C11.6421 15 15 11.6421 15 7.5H14ZM7.5 1C11.0899 1 14 3.91015 14 7.5H15C15 3.35786 11.6421 0 7.5 0V1ZM7.5 0C3.35786 0 0 3.35786 0 7.5H1C1 3.91015 3.91015 1 7.5 1V0ZM5 12V4.5H4V12H5ZM4.09466 4.79275L10.5947 13.7927L11.4053 13.2073L4.90534 4.20725L4.09466 4.79275ZM10 4V10H11V4H10Z"
              />
            </svg>

            <p>Next.js</p>
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
        <ul class="music" :style="{ color: darkBlue }">
          <h2><i class="fas fa-music"></i></h2>
          <li>
            <a
              :style="{ color: darkBlue }"
              rel="noopener noreferrer"
              target="_blank"
              href="https://open.spotify.com/artist/0L8ExT028jH3ddEcZwqJJ5?si=q1xvTHkkTTWSqvP52sFmmg&dl_branch=1"
              >Red Hot Chilli Peppers</a
            >
          </li>
          <li>
            <a
              :style="{ color: darkBlue }"
              rel="noopener noreferrer"
              target="_blank"
              href="https://open.spotify.com/artist/3MATPJ9tYbcMhw5VOZrRU6?si=RDo3zv7hSxKVNnuAvwspHQ&dl_branch=1"
              >Summer Salt</a
            >
          </li>
          <li>
            <a
              :style="{ color: darkBlue }"
              rel="noopener noreferrer"
              target="_blank"
              href="https://open.spotify.com/artist/7wbkl3zgDZEoZer357mVIw?si=Cm5BTNqzRbGlgq0XdUa_ZQ&dl_branch=1"
              >Boy Pablo</a
            >
          </li>
          <li>
            <a
              :style="{ color: darkBlue }"
              rel="noopener noreferrer"
              target="_blank"
              href="https://open.spotify.com/artist/3BR3Qfra04DICDUB2BL3eu?si=KGtSyrWOSwKLXpcy-Z65EQ&dl_branch=1"
              >Men on the couch</a
            >
          </li>
          <li>
            <a
              :style="{ color: darkBlue }"
              rel="noopener noreferrer"
              target="_blank"
              href="https://open.spotify.com/artist/5p0zkKpBuRguKebwRe0RI2?si=bMgvegk3R6G10ZP6f7kvGg&dl_branch=1"
              >Pierce Fulton</a
            >
          </li>
          <li>
            <a
              :style="{ color: darkBlue }"
              rel="noopener noreferrer"
              target="_blank"
              href="https://open.spotify.com/artist/2SdOKxC1sSxEyv8JYERaNe?si=khNCyTwzRwmGyZXaXDWdqA&dl_branch=1"
              >RuPaul</a
            >
          </li>
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
      <h1 :style="{ backgroundColor: white }">
        Let's create cool things together
      </h1>
      <h3 :style="{ backgroundColor: white }">
        Stay creative and have a stunning {{ weekDayOfToday }}!
      </h3>
      <div class="content" :style="{ backgroundColor: white }">
        <div class="cta">
          <video id="video" autoplay="true" muted="true" loop="true">
            <source src="@/assets/brofist.mp4" type="video/mp4" />
          </video>
        </div>
        <div class="socials">
          <a
            class="github"
            href="https://github.com/MrValraven"
            target="_blank"
            rel="noopener noreferrer"
            :style="{ color: darkBlue }"
          >
            <i
              id="github"
              class="fab fa-github"
              :style="{ color: darkBlue }"
            ></i>
            <p>@MrValraven</p>
          </a>
          <a
            class="linkedInA"
            href="https://www.linkedin.com/in/tiago-costa-b141121b1/"
            target="_blank"
            rel="noopener noreferrer"
            :style="{ color: darkBlue }"
          >
            <i
              id="linkedin"
              class="fab fa-linkedin"
              :style="{ color: darkBlue }"
            ></i>
            <p>Tiago Costa</p>
          </a>
          <a class="discord" @click="copyDiscord" :style="{ color: darkBlue }">
            <i
              id="discord"
              class="fab fa-discord"
              :style="{ color: darkBlue }"
            ></i>
            <p id="discordID">Valraven#7264</p>
          </a>
        </div>
        <form @submit.prevent="sendEmail">
          <label for="contactName" :style="{ color: darkBlue }">Name</label>
          <input
            type="text"
            v-model="contactName"
            required
            name="contactName"
          />
          <label for="contactEmail" :style="{ color: darkBlue }">Email</label>
          <input
            type="email"
            v-model="contactEmail"
            required
            name="contactEmail"
          />
          <label for="contactMessage" :style="{ color: darkBlue }"
            >Message</label
          >
          <textarea
            type="text"
            v-model="contactMessage"
            required
            name="contactMessage"
          />
          <Button
            class="contactButton"
            :buttonText="sendingButton"
            :style="{
              backgroundColor: darkBlue,
              color: whiteBlue,
              borderColor: normalBlue,
            }"
          />
        </form>
      </div>
      <div
        v-if="openNotification"
        class="notification"
        :style="{ backgroundColor: darkBlue, color: whiteBlue }"
      >
        <p>DiscordID copied sucessfully</p>
        <i @click="openNotification = false" class="fas fa-times"></i>
      </div>
    </section>
    <section class="frases" v-if="finished">
      <h1>
        video / seccao sobre todo o processo de construçao dos websites e
        processo criativo e tecnico
      </h1>
      <h1>video of myself being a retard</h1>
      <h1>It's important to think outside of the box</h1>
      <h1>show personality</h1>
    </section>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Navbar from "../components/Navbar.vue";
import SideProject from "../components/SideProject.vue";
import NavbarMobile from "../components/NavbarMobile.vue";
import ScrollToTopButton from "../components/ScrollToTopButton.vue";
import Button from "../components/Button.vue";
import gsap from "gsap";

export default defineComponent({
  name: "Home",
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
    const beforeEnter: any = (el: any) => {
      el.style.opacity = 0;
      el.style.transform =
        "rotate(-5deg) scale(1.1, 1.1) translateX(-10px) translateY(-10px)";
    };
    const enter: any = (el: any, done: any) => {
      gsap.to(el, {
        opacity: 1,
        x: 0,
        y: 0,
        rotation: 0,
        duration: 1,
        scale: 1,
        ease: "power3",
        onComplete: done,
        delay: el.dataset.index * 0.1,
      });
    };
    return { chars, chars2, beforeEnter, enter };
  },
  data() {
    return {
      sideprojects: [
        {
          id: "1",
          title: "Kucomcu.io Smart Contract",
          description: "The smart contract implementation for Kucomcu.io",
          websiteURL:
            "https://ropsten.etherscan.io/address/0x655B3E27cE170F8E30010E3dfa7AA43B1E7e8B72",
          codeURL: "https://github.com/MrValraven/kucomcu-smart_contract",
        },
        {
          id: "2",
          title: "AAUE.pt Backend (WiP)",
          description:
            "Backend with User auth (JWT), MongoDB integration with user and news models",
          websiteURL: "https://aaue.pt/noticias",
          codeURL: "https://github.com/MrValraven/blog-API",
        },
        {
          id: "2.2",
          title: "BottleCellar.io",
          description:
            "A small project I did for a React + Redux Frontend Developer assessment test",
          websiteURL: "https://bottlecellar.vercel.app",
          codeURL: "https://github.com/MrValraven/bottlecellar",
        },
        {
          id: "2.5",
          title: "Crown Clothing (WiP)",
          description:
            "A fictional clothing Ecommerce, built this to learn React, React Router, Redux, Hooks, Firebase and Stripe API",
          websiteURL: "https://crownclothingecom.vercel.app",
          codeURL: "https://github.com/MrValraven/clothing-ecommerce",
        },
        {
          id: "3",
          title: "Web Scraper",
          description:
            "Web Scraper that gets all the housing listings from alojamento.aaue.pt",
          websiteURL:
            "https://dados-portal-alojamento.herokuapp.com/getAnuncios",
          codeURL: "https://github.com/MrValraven/alojamento-web-scraper",
        },
        {
          id: "4.5",
          title: "Sapatuna - Party Game (WiP)",
          description: "A LGBTQI+ friendly truth or dare game",
          websiteURL: "https://sapatuna.vercel.app/",
          codeURL: "https://github.com/MrValraven/sapatuna",
        },
        {
          id: "4",
          title: "NEEI.UE (WiP)",
          description:
            "A website for the University of Évora's Computer Science Club",
          websiteURL: "https://neei.vercel.app/",
          codeURL: "https://github.com/MrValraven/neei",
        },
        {
          id: "4.1",
          title: "Lost World (WiP)",
          description: "A E-commerce website for the Lost World store in Sines",
          websiteURL: "https://lostworldcomics.netlify.app/",
          codeURL: "https://github.com/MrValraven/lostworld",
        },
        {
          id: "4.5",
          title: "Splitter",
          description:
            "A Tip calculator app built with Vue.js. This is a challenge from Frontend Mentor.",
          websiteURL: "https://splitterapp.netlify.app/#/",
          codeURL: "https://github.com/MrValraven/spliter",
        },
        {
          id: "5",
          title: "Quote Generator",
          description: "A quote generator",
          websiteURL: "https://mrvalraven-quote-generator.netlify.app/",
          codeURL: "https://github.com/MrValraven/Quote-generator",
        },
        {
          id: "6",
          title: "Infinite Scroller",
          description: "Infinite scroller using the Unsplash API",
          websiteURL: "https://mrvalraven-infinite-scroller.netlify.app/",
          codeURL: "https://github.com/MrValraven/Infinite-Scroll",
        },
        {
          id: "7",
          title: "Picture-in-Picture",
          description:
            "A simple project to try out the picture-in-picture feature",
          websiteURL: "https://mrvalraven-pictureinpicture.netlify.app/",
          codeURL: "https://github.com/MrValraven/Picture-in-Picture",
        },
        {
          id: "8",
          title: "Reddit CLI",
          description:
            "A simple reddit CLI that opens a random post from reddit's front page",
          websiteURL: "",
          codeURL: "https://github.com/MrValraven/reddit-cli",
        },
        {
          id: "9",
          title: "Perspective Playground",
          description:
            "A perspective playground to test how Vue's v-model works",
          websiteURL: "https://perspectiveplayground.netlify.app/",
          codeURL: "https://github.com/MrValraven/perspective-playground",
        },
      ],
      currentSideprojectsLength: 6,
      activatedNavbar: false,
      isAtTop: true,
      mobileMode: false,
      finished: false,
      isOnTeto: false,
      isOnKucomcu: false,
      isOnAAUE: false,
      isOnReitor: false,
      isOnExpo: false,
      opacityTeto: 0,
      opacityKucomcu: 0,
      opacityAAUE: 0,
      opacityReitor: 0,
      opacityExpo: 0,
      activateTyping: true,
      codeEnd: false,
      lineNumbers: [121],
      image:
        "https://i.pinimg.com/originals/e3/66/87/e366871039caf5afd17b0bcfecb453cb.jpg",
      contactName: "",
      contactEmail: "",
      contactMessage: "",
      weekDayOfToday: "",
      openNotification: false,
      isDarkMode: false,
      theme: "light",
      whiteBlue: "#E7ECEF",
      darkBlue: "#274C77",
      normalBlue: "#6aa7cf",
      lightBlue: "#A3CEF1",
      editorBlue: "#21313c",
      gostoDesteAzul: "#aedbf7",
      white: "#FFFFFF",
      sendingButton: "Send message",
    };
  },
  components: {
    Navbar,
    NavbarMobile,
    ScrollToTopButton,
    Button,
    SideProject,
  },
  created() {
    window.addEventListener("scroll", this.handleScroll);
    this.handleResize();
    window.addEventListener("resize", this.handleResize);
    const currentTheme = localStorage.getItem("theme")!;
    this.checkTheme(currentTheme);
    for (let i: number = 122; i < 146; i++) {
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
    window.removeEventListener("scroll", this.handleScroll);
    window.removeEventListener("resize", this.handleResize);
  },
  methods: {
    showAllProjects() {
      this.currentSideprojectsLength = this.sideprojects.length;
    },
    getImgURL(image: String) {
      return require("../assets/" + image);
    },
    scrollToElement(destination: string) {
      const element = document.querySelector(destination);
      if (element) {
        element.scrollIntoView({ behavior: "smooth" });
      }
    },
    handleScroll() {
      window.pageYOffset >= 250
        ? (this.isAtTop = false)
        : (this.isAtTop = true);

      let tetoProjectHeight = document
        .querySelector(".seistetos")
        ?.getBoundingClientRect().top;
      tetoProjectHeight = Number(tetoProjectHeight);

      if (window.pageYOffset >= tetoProjectHeight - 400) {
        this.isOnTeto = true;
        this.opacityTeto = 1;
      }

      let kucomcuProjectHeight = document
        .querySelector(".kucomcu")
        ?.getBoundingClientRect().top;
      kucomcuProjectHeight = Number(kucomcuProjectHeight);

      if (window.pageYOffset >= kucomcuProjectHeight + 1000) {
        this.isOnKucomcu = true;
        this.opacityKucomcu = 1;
      }
      let aaueProjectHeight = document
        .querySelector(".aaue")
        ?.getBoundingClientRect().top;
      aaueProjectHeight = Number(aaueProjectHeight);

      if (window.pageYOffset >= aaueProjectHeight + 200) {
        this.isOnAAUE = true;
        this.opacityAAUE = 1;
      }
      let reitorProjectHeight = document
        .querySelector(".reitor")
        ?.getBoundingClientRect().top;
      reitorProjectHeight = Number(reitorProjectHeight);

      if (window.pageYOffset >= reitorProjectHeight + 200) {
        this.isOnReitor = true;
        this.opacityReitor = 1;
      }
      let expoProjectHeight = document
        .querySelector(".expoestudante")
        ?.getBoundingClientRect().top;
      expoProjectHeight = Number(expoProjectHeight);

      if (window.pageYOffset >= expoProjectHeight + 2000) {
        this.isOnExpo = true;
        this.opacityExpo = 1;
      }

      let aboutMeHeight = document
        .querySelector(".aboutMe")
        ?.getBoundingClientRect().top;
      aboutMeHeight = Number(aboutMeHeight);

      if (aboutMeHeight < 650 && this.activateTyping) {
        this.typeAllCode();
        this.activateTyping = false;
      }
    },
    handleResize() {
      this.mobileMode = window.innerWidth <= 1015;
      if (!this.mobileMode) {
        this.activatedNavbar = false;
      }
    },

    async sleepNow(delay: number) {
      return new Promise((resolve) => setTimeout(resolve, delay));
    },

    async typeCode(element: string, word: string) {
      let selectedElement = document.querySelector(element)!;

      let index = 0;
      let maxIndex = word.length;
      let letter = "";

      while (index <= maxIndex) {
        await this.sleepNow(20);
        letter = word.slice(0, index);
        selectedElement.textContent = letter;
        index++;
      }
    },

    async typeAllCode() {
      let delay = 0;

      let arrayOfElements = [
        { element: ".const", text: "const" },
        { element: "#me", text: " me" },
        { element: "#igual1", text: " = " },
        { element: "#chavetas1", text: "{" },
        { element: "#nome", text: "name" },
        { element: "#doisPontos1", text: ": " },
        { element: "#Tiago", text: '"Tiago"' },
        { element: "#virgula1", text: "," },
        { element: "#age", text: "favoriteFandom" },
        { element: "#doisPontos2", text: ": " },
        { element: "#idade", text: '"Star Wars"' },
        { element: "#virgula2", text: "," },
        { element: "#role", text: "role" },
        { element: "#doisPontos3", text: ": " },
        { element: "#fullstack", text: '"Fullstack Developer"' },
        { element: "#virgula3", text: "," },
        { element: "#git", text: "github" },
        { element: "#doisPontos4", text: ": " },
        { element: "#githubLink", text: '"https://github.com/MrValraven"' },
        { element: "#virgula4", text: "," },
        { element: "#IDE", text: "IDE" },
        { element: "#doisPontos5", text: ": " },
        { element: "#vscode", text: '"Visual Studio Code"' },
        { element: "#chavetas2", text: "}" },
        { element: "#class", text: "class" },
        { element: "#toolset", text: " Toolset" },
        { element: "#chavetas3", text: " {" },
        { element: "#skills", text: "skills" },
        { element: "#doisPontos6", text: ": " },
        { element: "#chavetas4", text: " {" },
        { element: "#icon1", text: " icon" },
        { element: "#doisPontos7", text: ": " },
        { element: "#string1", text: "string" },
        { element: "#virgula4", text: "," },
        { element: "#name2", text: " name" },
        { element: "#doisPontos8", text: ": " },
        { element: "#string2", text: "string" },
        { element: "#chavetas5", text: " }" },
        { element: "#array1", text: "[" },
        { element: "#array2", text: "]" },
        { element: "#pontovirgula1", text: ";" },
        { element: "#constructor", text: "constructor" },
        { element: "#parenteses1", text: "(" },
        { element: "#skillset", text: "skillset" },
        { element: "#doisPontos9", text: ":" },
        { element: "#chavetas6", text: " {" },
        { element: "#icon2", text: " icon" },
        { element: "#doisPontos10", text: ": " },
        { element: "#string3", text: "string" },
        { element: "#virgula5", text: "," },
        { element: "#name3", text: " name" },
        { element: "#doisPontos11", text: ": " },
        { element: "#string4", text: "string" },
        { element: "#chavetas7", text: " }" },
        { element: "#array3", text: "[" },
        { element: "#array4", text: "]" },
        { element: "#parenteses2", text: ")" },
        { element: "#chavetas8", text: " {" },
        { element: "#this1", text: " this" },
        { element: "#ponto1", text: "." },
        { element: "#skills2", text: "skills" },
        { element: "#ponto2", text: "." },
        { element: "#push", text: "push" },
        { element: "#parenteses3", text: "(" },
        { element: "#reticencias", text: "..." },
        { element: "#skillset2", text: "skillset" },
        { element: "#parenteses4", text: ")" },
        { element: "#pontovirgula2", text: ";" },
        { element: "#chavetas9", text: " {" },
        { element: "#display", text: "display" },
        { element: "#parenteses5", text: "(" },
        { element: "#parenteses6", text: ")" },
        { element: "#chavetas10", text: " {" },
        { element: "#for", text: "for" },
        { element: "#parenteses7", text: "(" },
        { element: "#let", text: "let " },
        { element: "#skill1", text: "skill " },
        { element: "#in", text: "in " },
        { element: "#this2", text: "this" },
        { element: "#ponto3", text: "." },
        { element: "#skills3", text: "skills" },
        { element: "#parenteses8", text: ")" },
        { element: "#chavetas11", text: " {" },
        { element: "#console", text: "console" },
        { element: "#ponto4", text: "." },
        { element: "#log", text: "log" },
        { element: "#parenteses9", text: "(" },
        { element: "#skill2", text: "skill" },
        { element: "#parenteses20", text: ")" },
        { element: "#pontovirgula3", text: ";" },
        { element: "#chavetas12", text: "}" },
        { element: "#chavetas13", text: "}" },
        { element: "#chavetas14", text: "}" },
        { element: "#export", text: "export " },
        { element: "#chavetas15", text: "{" },
        { element: "#toolset2", text: " Toolset " },
        { element: "#chavetas16", text: "}" },
        { element: "#pontovirgula4", text: ";" },
        { element: "#import", text: "import" },
        { element: "#chavetas17", text: " { " },
        { element: "#toolset4", text: "Toolset" },
        { element: "#chavetas18", text: " } " },
        { element: "#from", text: "from " },
        { element: "#home", text: '"./Home.vue"' },
        { element: "#pontovirgula5", text: ";" },
        { element: "#const2", text: "const " },
        { element: "#toolset5", text: "toolset " },
        { element: "#igual2", text: "= " },
        { element: "#new", text: "new " },
        { element: "#toolset6", text: "Toolset" },
        { element: "#parenteses21", text: "(" },
        { element: "#currentSkills", text: "currentSkills" },
        { element: "#parenteses22", text: ")" },
        { element: "#pontovirgula6", text: ";" },
        { element: "#toolsetFinal", text: "toolset" },
        { element: "#ponto5", text: "." },
        { element: "#display2", text: "display()" },
        { element: "#pontovirgula7", text: ";" },
      ];

      for (let i = 0; i < arrayOfElements.length; i++) {
        await this.typeCode(
          arrayOfElements[i].element,
          arrayOfElements[i].text
        );

        if (i % 4 === 0) {
          await this.sleepNow(delay);
        }
      }

      await this.sleepNow(delay);
      this.codeEnd = true;
      await this.typeCode(
        ".lastp",
        "PS C:\\Users\\tiagoCosta\\Desktop\\Trabalhos\\portefolio>"
      );
    },
    async copyDiscord() {
      let copyText = document.getElementById("discordID")!;

      let input = document.createElement("textarea");

      input.value = copyText.textContent!;
      document.body.appendChild(input);
      input.select();
      document.execCommand("Copy");

      input.remove();

      this.openNotification = true;

      setTimeout(() => {
        this.openNotification = false;
      }, 10000);
    },
    checkTheme(theme: string) {
      if (theme === null) {
        this.theme = "light";
      } else {
        this.theme = theme;
      }

      if (this.theme === "light") {
        this.whiteBlue = "#E7ECEF";
        this.darkBlue = "#274C77";
        this.normalBlue = "#6aa7cf";
        this.lightBlue = "#A3CEF1";
        this.editorBlue = "#21313c";
        this.gostoDesteAzul = "#aedbf7";
        this.white = "#FFFFFF";
        this.isDarkMode = false;
      } else {
        this.whiteBlue = "#0e1720";
        this.darkBlue = "#E7ECEF";
        this.normalBlue = "#E7ECEF";
        this.white = "#274C77";
        this.isDarkMode = true;
      }
    },
    toggleDarkMode() {
      this.theme === "light" ? (this.theme = "dark") : (this.theme = "light");

      this.checkTheme(this.theme);

      localStorage.setItem("theme", this.theme);
    },
    sendEmail() {
      if (
        this.contactName === "" ||
        this.contactMessage === "" ||
        this.contactEmail === ""
      ) {
        return;
      }

      this.sendingButton = "Sending message...";

      const message = {
        to: "akatiago@gmail.com",
        from: "akatiago@gmail.com",
        subject: this.contactName,
        text: this.contactMessage,
        html: this.contactMessage + " " + this.contactEmail,
      };

      const requestOptions = {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(message),
      };
      fetch(
        "https://send-personal-email-api.herokuapp.com/sendemail",
        requestOptions
      )
        .then((response) => response.json())
        .then(() => {
          this.contactEmail = "";
          this.contactName = "";
          this.contactMessage = "";
          this.sendingButton = "Send message";
        })
        .catch((err) => {
          console.log(err);
          this.sendingButton = "An error has occurred";
          setTimeout(() => {
            this.contactEmail = "";
            this.contactName = "";
            this.contactMessage = "";
            this.sendingButton = "Send message";
          }, 5000);
        });
    },
  },
});
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css?family=Roboto:700");
@keyframes showTopText {
  0% {
    transform: translate3d(0, 100%, 0);
  }

  100% {
    transform: translate3d(0, 0, 0);
  }
}
@keyframes showBottomText {
  0% {
    transform: translate3d(0, -300%, 0);
  }
  100% {
    transform: translate3d(0, 0, 0);
  }
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
      box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px,
        rgba(0, 0, 0, 0.3) 0px 30px 60px -30px,
        rgba(10, 37, 64, 0.35) 0px -2px 6px 0px inset;
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

        #eth {
          position: absolute;
          height: 300px;
          left: 36.5%;
          bottom: 5%;
        }
        #aaue {
          position: absolute;
          height: 200px;
          left: 39.5%;
          bottom: 6.7%;
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
          animation: showTopText 1s 1s forwards;
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

  .sideprojects {
    display: flex;
    flex-direction: column;
    padding-top: 0;
    padding-bottom: 100px;

    h1 {
      text-transform: uppercase;
      font-size: 60px;
    }

    .container {
      display: flex;
      flex-wrap: wrap;
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
        font-weight: 300;
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
          color: $whiteBlue;
          transform: scale(0);

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
            transition: opacity 0.2s cubic-bezier(0.075, 0.82, 0.165, 1),
              transform 0.2s cubic-bezier(0.075, 0.82, 0.165, 1);
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
          animation: scaleUp $delay 1.5s cubic-bezier(0.075, 0.82, 0.165, 1)
            forwards;
        }
        .css {
          animation: scaleUp $delay 2s cubic-bezier(0.075, 0.82, 0.165, 1)
            forwards;
        }
        .sass {
          animation: scaleUp $delay 2.5s cubic-bezier(0.075, 0.82, 0.165, 1)
            forwards;
        }
        .js {
          animation: scaleUp $delay 3s cubic-bezier(0.075, 0.82, 0.165, 1)
            forwards;
        }
        .ts {
          animation: scaleUp $delay 3.5s cubic-bezier(0.075, 0.82, 0.165, 1)
            forwards;
        }
        .vue {
          animation: scaleUp $delay 4s cubic-bezier(0.075, 0.82, 0.165, 1)
            forwards;
        }
        .node {
          animation: scaleUp $delay 4.5s cubic-bezier(0.075, 0.82, 0.165, 1)
            forwards;
        }
        .npm {
          animation: scaleUp $delay 5s cubic-bezier(0.075, 0.82, 0.165, 1)
            forwards;
        }
        .yarn {
          animation: scaleUp $delay 5.5s cubic-bezier(0.075, 0.82, 0.165, 1)
            forwards;
        }
        .gitalt {
          animation: scaleUp 1s 6s cubic-bezier(0.075, 0.82, 0.165, 1) forwards;
        }
        .sql {
          animation: scaleUp 1s 6.5s cubic-bezier(0.075, 0.82, 0.165, 1)
            forwards;
        }
        .redux {
          animation: scaleUp 1s 7s cubic-bezier(0.075, 0.82, 0.165, 1) forwards;
        }
        .nextjs {
          animation: scaleUp 1s 7.5s cubic-bezier(0.075, 0.82, 0.165, 1)
            forwards;
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
      border-radius: 12px 12px 0 0;
      opacity: 1;
    }

    h3 {
      margin-top: -10px;
      padding-bottom: 10px;
      background-color: white;
      filter: grayscale(0%);
      padding-left: 55px;
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

      i {
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
          #hoverExpo,
          #aaue,
          #eth {
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
      h1 {
        line-height: 70px;
        padding-bottom: 30px;
      }
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

    .sideprojects h1 {
      font-size: 42px;
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

    .about .card .editor .lineNumbers p {
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
        margin-top: -100px;
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
