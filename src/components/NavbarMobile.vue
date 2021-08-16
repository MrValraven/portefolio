<template>
    <nav class="mobileNav">
        <transition-group
        v-if="isActive" 
        appear
        tag="ul"
        @before-enter="beforeEnter"
        @enter="enter" 
        class="navLinks" 
        :class="isActive"
        :style="{backgroundColor: backgroundColor}"
        >
            <li v-for="(navlink, index) in navLinks" :key="navlink.id" :data-index="index"  @click="this.$emit(navlink.emitter), toggleClass()" ><router-link :style="{color: textColor}" :to="{ name: navlink.routeName }"> {{ navlink.routeText }}</router-link></li>
        </transition-group>

        <div class="burger" @click="toggleClass()">
            <div v-if="!isActive" class="burgerText" :style="{color: textColor}">MENU</div>
            <div class="drawing" :class="newClass">
                <div class="line1" :style="{backgroundColor: textColor}"></div>
                <div class="line2" :style="{backgroundColor: textColor}"></div>
                <div class="line3" :style="{backgroundColor: textColor}"></div>
            </div>
        </div>
       
    </nav>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import gsap from 'gsap';
export default defineComponent({          
    setup() {
        const navLinks = [
            {id: 0, routeName: "Home", routeText: ".home()", emitter: 'home'},
            {id: 1, routeName: "Home", routeText: ".work()", emitter: 'work'},
            {id: 2, routeName: "Home", routeText: ".about()", emitter: 'about'},
            {id: 3, routeName: "Home", routeText: ".contacts()", emitter: 'contacts'},
            {id: 4, routeName: "Home", routeText: ".curriculumVitae()"},
        ]
        const beforeEnter: any = (el: any) => {
            el.style.opacity = 0;
            el.style.transform = 'translateX(-100px)';
        }
        const enter: any = (el: any, done: any) => {
            gsap.to(el, {
                opacity: 1,
                x: 0,
                duration: 0.2,
                onComplete: done,
                delay: el.dataset.index * 0.05,
            });
        }
        return { navLinks, beforeEnter, enter }
    },
    name: "MobileNav",
    data() {
        return {
            toggle: false,
            newClass: "",
            isActive: "",
            activatedNavbar: false,
        }
    },
    props: {
        textColor: String,
        backgroundColor: String,
    },
    emits: ['home','work','about','contacts', 'toggleTheme', 'activatedNavbar'],
    methods: {
        toggleClass() {
            this.toggle = !this.toggle;
            this.toggle ? this.newClass = "toggle" : this.newClass = "";
            this.toggle ? this.isActive = "isActive" : this.isActive = "";
            this.$emit("activatedNavbar", this.activatedNavbar);
        },
    },
});
</script>

<style lang="scss">
body {
		overflow-x: hidden;
	}
.mobileNav {
    position: absolute;
	z-index: 10;
	width: 100%;
	opacity: 1;
	color: #000;
	padding: 35px 100px 0;
    .navLinks {
        position: absolute;
        right: 0px;
        height: 100vh;
        top: 0vh;
        display: none;
        flex-direction: column;
        align-items: center;
        background-color: #040427;
        justify-content: space-around;
        opacity: 0;
        width: 100%;
        transition: all 0.4s ease-in;
        li {
            opacity: 1;
            font-size: 20px;
            a {
                font-family: monospace;
                color: white;
            }
        }
	}
    
    .isActive {
        position: fixed;
        transform: translateX(0%);
        display: flex;
        opacity: 1;
    }
    .burger {
        display: flex;
        align-items: center;
        cursor: pointer;
        position: absolute;
        top: 20px;
        right: 20px;
        .burgerText {
            font-size: 20px;
            letter-spacing: 3px;
        }
        .drawing div{
            width: 35px;
            height: 3px;
            margin: 5px;
            transition: all 0.3s ease;
        }
         .toggle {
            .line1 {
                background-color: white;
                transform: rotate(-45deg) translate(-5px, 6px);
            }
            .line2 {
                opacity: 0;
            }
            .line3 {
                background-color: white;
                transform: rotate(45deg) translate(-5px, -6px);
            }
            
        }
    }
}
</style>