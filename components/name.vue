<template>
    <h1 title="Frederic Köberl" class="name">
    <span data-nosnippet>
      <client-only>
        Fred<span class="default">eric</span>
        K<span class="default">ö</span><span class="hidden">oe</span>berl
      </client-only>
    </span>
        <span v-show="!init">Frederic Köberl</span>
    </h1>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const init = ref(false);
onMounted(() => {
    init.value = true;
});
</script>

<style>
.name {
    margin: -40px;
    padding: 60px 40px 40px 40px;
    --animation-duration: 0.5s;
}

.name .default,
.name .hidden {
    display: inline-block;
    transition: font-size var(--animation-duration), opacity var(--animation-duration);
}

.name .default {
    user-select: all;
    opacity: 1;
}

.name .hidden {
    font-size: 0;
    user-select: none;
    opacity: 0;
}

.name:hover .default {
    font-size: 0;
    user-select: none;
    opacity: 0;
}

.name:hover .hidden {
    font-size: inherit;
    user-select: all;
    opacity: 1;
}
</style>
