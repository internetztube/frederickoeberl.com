<template>
  <main>
    <section class="content" @click="setRandomColorPairs">
      <name />
      <slogan />
      <social class="content-block" />
      <contact class="content-block" />
      <projects class="content-block" />
    </section>
    <picture class="background" :style="`--primary: ${colors.primary}; --secondary: ${colors.secondary}`">
      <img src="https://source.unsplash.com/user/internetztube?1" alt="random Unsplash photo">
    </picture>
  </main>
</template>

<script>
import name from '../components/name'
import slogan from '../components/slogan'
import social from '../components/social'
import contact from '../components/contact'
import projects from '../components/projects'

export default {
  components: { name, slogan, social, contact, projects },
  data () {
    return { colors: { primary: '#2d6a4f', secondary: '#0f405c' } }
  },
  computed: {
    colorPairs () {
      return [
        ['#0f405c', '#E64C4C'],
        ['#4E2BCC', '#5f0f57'],
        ['#289DCC', '#B31919'],
        ['#2d6a4f', '#9119B3'],
        ['#9a031e', '#B620E0'],
        ['#815EFF', '#FB8332']
      ]
    }
  },
  mounted () {
    this.setRandomColorPairs()
  },
  methods: {
    shuffleArray (a) {
      for (let i = a.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [a[i], a[j]] = [a[j], a[i]]
      }
      return a
    },
    setRandomColorPairs () {
      const shuffledColorPairs = this.shuffleArray(this.colorPairs)
      this.colors = { primary: shuffledColorPairs[0][0], secondary: shuffledColorPairs[0][1] }
    }
  }
}
</script>

<style lang="scss" scoped>

main {
  min-height: 100%;
  position: relative;
}

.content {
  padding: 40px;
  min-height: 100vh;
  line-height: 1.7;
  background:
    linear-gradient(
      135deg,
      rgba(17, 17, 17, 1) 0%,
      rgba(17, 17, 17, 1) 15%,
      rgba(17, 17, 17, 0.2539390756302521) 100%
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

  img {
    height: 100%;
    width: 100%;
    object-fit: cover;
    mix-blend-mode: lighten;
  }

  &:before,
  &:after {
    content: "";
    position: absolute;
    inset: 0;
    z-index: -1;
    transition: background 1s;
  }

  &:before {
    background: var(--primary);
    mix-blend-mode: screen;
  }

  &:after {
    background: var(--secondary);
    mix-blend-mode: luminosity;
  }
}


</style>
