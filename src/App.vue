<script setup>

import { ref, onMounted, onUnmounted } from 'vue';

const showMenu = ref(false);
function toggleMenu() {
    showMenu.value = !showMenu.value;
}
import About from './sections/about.vue';
import Contact from './sections/contact.vue';
import Products from './sections/products.vue';
import Services from './sections/services.vue';

const sections = [
    { id: 'home', label: 'Home', icon: 'home-outline' },
    { id: 'about', label: 'About', icon: 'information-circle-outline' },
    { id: 'services', label: 'Services', icon: 'construct-outline' },
    { id: 'products', label: 'Products', icon: 'cube-outline' },
    { id: 'contact', label: 'Contact', icon: 'call-outline' }
];
const activeSection = ref('');

function scrollToSection(id) {
    const el = document.getElementById(id);
    if (el) {
        el.scrollIntoView({ behavior: 'smooth', block: 'start' });
    }
}

function updateActiveSection() {
    let found = '';
    for (const section of sections) {
        const el = document.getElementById(section.id);
        if (el) {
            const rect = el.getBoundingClientRect();
            if (rect.top <= 80 && rect.bottom > 80) {
                found = section.id;
                break;
            }
        }
    }
    activeSection.value = found;
}

onMounted(() => {
    window.addEventListener('scroll', updateActiveSection);
    updateActiveSection();
});
onUnmounted(() => {
    window.removeEventListener('scroll', updateActiveSection);
});

</script>

<template>


        <nav class="navBar">
            <div class="navBar__container">
                <button class="navBar__hamburger" @click="toggleMenu" aria-label="Toggle menu">
                    <span :class="{ open: showMenu }"></span>
                    <span :class="{ open: showMenu }"></span>
                    <span :class="{ open: showMenu }"></span>
                </button>
                            <ul :class="{ open: showMenu }">
                                    <li v-for="section in sections" :key="section.id">
                                            <button
                                                :class="{ selected: activeSection === section.id }"
                                                @click="scrollToSection(section.id); showMenu = false;"
                                            >
                                                <ion-icon :name="section.icon" style="vertical-align: middle; margin-right: 8px; font-size: 1.2em;"></ion-icon>
                                                {{ section.label }}
                                            </button>
                                    </li>
                            </ul>
            </div>
        </nav>


    <div class="firstSection fade-in" id="home">
        <div class="firstSection_content">
            <div class="MainLogo fade-in">
                <img src="/public/resources/VARIANTES/MainLogoBlueNoTitle.png" alt="Logo">
            </div>
            <div class="fade-in">
                <h1>Olympus DCM</h1>
                <p>IT Consulting services, architecture solutions and tailored software of the best quality, your success is our priority.</p>
            </div>
        </div>
    </div>
    <section id="about" class="fade-in"><About /></section>
    <section id="services" class="fade-in"><Services /></section>
    <section id="products" class="fade-in"><Products /></section>
    <section id="contact" class="fade-in"><Contact /></section>


<!-- 


 -->




</template>

<style scoped lang="scss">


.navBar {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background-color: #333;
    color: white;
    z-index: 1000;
    .navBar__container {
        display: flex;
        align-items: center;
        justify-content: center;
        max-width: 1200px;
        margin: 0 auto;
        padding: 0 20px;
        height: 60px;
        position: relative;
    }
    .navBar__hamburger {
        display: none;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 40px;
        height: 40px;
        background: none;
        border: none;
        cursor: pointer;
        span {
            display: block;
            width: 28px;
            height: 4px;
            margin: 4px 0;
            background: #fff;
            border-radius: 2px;
            transition: 0.3s;
        }
        span.open:nth-child(1) {
            transform: translateY(8px) rotate(45deg);
        }
        span.open:nth-child(2) {
            opacity: 0;
        }
        span.open:nth-child(3) {
            transform: translateY(-8px) rotate(-45deg);
        }
    }
    ul {
        display: flex;
        justify-content: center;
        list-style-type: none;
        padding: 0;
        margin: 0;
        li {
            margin: 0 20px;
            font-family: 'Inter', sans-serif;
            button {
                background: none;
                border: none;
                color: white;
                font-size: 1rem;
                cursor: pointer;
                padding: 8px 16px;
                border-radius: 4px;
                transition: background 0.2s, color 0.2s;
                &.selected {
                    background: #fff;
                    color: #333;
                    font-weight: bold;
                }
                &:hover {
                    background: #555;
                }
            }
        }
    }
    @media (max-width: 900px) {
        .navBar__container {
            height: 56px;
        }
        .navBar__hamburger {
            display: flex;
        }
        ul {
            position: absolute;
            top: 60px;
            left: 0;
            width: 100vw;
            background: #333;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
            padding: 0;
            margin: 0;
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease;
            li {
                margin: 16px 0;
            }
        }
        ul.open {
            max-height: 400px;
            padding-bottom: 20px;
        }
    }
}



.firstSection {
    width: 100%;
    margin: auto;
    padding-bottom: 200px;
    padding-top: 200px;
    font-family: 'Inter', sans-serif;
    .firstSection_content {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 50px;
        width: 100%;
        margin: auto;
        .MainLogo {
            width: 300px;
            height: 300px;
            display: flex;
            align-items: center;
            justify-content: center;
            img {
                width: 100%;
                height: auto;
                display: block;
                margin: 0 auto;
            }
        }
        h1 {
            color: rgb(0, 102, 204);
            font-size: 2.5rem;
            margin-bottom: 10px;
            text-align: center;
        }
        p {
            font-size: 1.2rem;
            color: #333;
            max-width: 300px;
            text-align: center;
        }
        @media (max-width: 900px) {
            flex-direction: column;
            gap: 20px;
            .MainLogo {
                margin-bottom: 20px;
            }
        }
    }
}


.fade-in {
    opacity: 0;
    transform: translateY(30px);
    animation: fadeInUp 1s ease forwards;
}
.firstSection.fade-in {
    animation-delay: 0.1s;
}
.MainLogo.fade-in {
    animation-delay: 0.2s;
}
.fade-in:not(.MainLogo):not(.firstSection) {
    animation-delay: 0.5s;
}

@keyframes fadeInUp {
    to {
        opacity: 1;
        transform: none;
    }
}
</style>