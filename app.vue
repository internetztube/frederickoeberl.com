<template>
    <main>
        <section class="content" @click="setRandomColorPairs">
            <Name/>
            <Slogan/>
            <Social class="content-block"/>
            <Contact class="content-block"/>
            <Projects class="content-block"/>
        </section>
        <picture class="background" :style="`--primary: ${colors.primary}; --secondary: ${colors.secondary}`">
            <img src="https://unsplash.internetztube.net/internetztube/full" alt="random Unsplash photo">
        </picture>
    </main>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import Name from '../components/name.vue';
import Slogan from '../components/slogan.vue';
import Social from '../components/social.vue';
import Contact from '../components/contact.vue';
import Projects from '../components/projects.vue';

const colors = ref({ primary: '#2d6a4f', secondary: '#0f405c' });

const colorPairs = [
    ['#0f405c', '#E64C4C'],
    ['#4E2BCC', '#5f0f57'],
    ['#289DCC', '#B31919'],
    ['#2d6a4f', '#9119B3'],
    ['#9a031e', '#B620E0'],
    ['#815EFF', '#FB8332']
];

const shuffleArray = (a) => {
    for (let i = a.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [a[i], a[j]] = [a[j], a[i]];
    }
    return a;
};

const setRandomColorPairs = () => {
    const shuffledColorPairs = shuffleArray(colorPairs);
    colors.value = { primary: shuffledColorPairs[0][0], secondary: shuffledColorPairs[0][1] };
};

onMounted(() => {
    setRandomColorPairs();
});

</script>

<style lang="css">

html {
    box-sizing: border-box;
    height: 100%;
    line-height: 0;
}

*,
*:before,
*:after {
    box-sizing: inherit;
}

body {
    font-family: Monaco, Consolas, Lucida Console, Andale Mono, monospace;
    color: #fff;
    background: #111;
    min-height: 100%;
    margin: 0;
}

#__nuxt,
#__layout {
    min-height: 100%;
}

a {
    color: #fff;
}

a:hover {
    text-decoration: none;
}

main {
    min-height: 100%;
    position: relative;
}

.content {
    padding: 40px;
    min-height: 100vh;
    line-height: 1.7;
    background: linear-gradient(
            135deg,
            rgba(17, 17, 17, 1) 0%,
            rgba(17, 17, 17, 1) 15%,
            rgba(17, 17, 17, 0.25) 100%
    );
}

.content-block {
    margin: 2em 0;
}

.background {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    isolation: isolate;
}

.background img {
    height: 100%;
    width: 100%;
    object-fit: cover;
    mix-blend-mode: lighten;
}

.background:before,
.background:after {
    content: "";
    position: absolute;
    inset: 0;
    z-index: -1;
    transition: background 1s;
}

.background:before {
    background: var(--primary);
    mix-blend-mode: screen;
}

.background:after {
    background: var(--secondary);
    mix-blend-mode: luminosity;
}
</style>
