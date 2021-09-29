<template>
  <h1 title="Frederic Köberl" class="name">
    <no-ssr>
      Fred<span class="default">eric</span>
      K<span class="default">ö</span><span class="hidden">oe</span>berl
    </no-ssr>
    <span v-show="!init">Frederic Köberl</span>
  </h1>
</template>

<script>
export default {
  data () {
    return { init: false }
  },
  mounted () {
    this.init = true
  }
}
</script>

<style lang="scss">
$animation-duration: 0.5s;

.name {
  margin: -40px;
  padding: 60px 40px 40px 40px;

  .default,
  .hidden {
    display: inline-block;
    transition: font-size $animation-duration, opacity $animation-duration;
  }

  .default {
    user-select: all;
    opacity: 1;
  }

  .hidden {
    font-size: 0;
    user-select: none;
    opacity: 0;
  }

  &:hover {
    .default {
      font-size: 0;
      user-select: none;
      opacity: 0;
    }

    .hidden {
      font-size: inherit;
      user-select: all;
      opacity: 1;
    }
  }
}
</style>
