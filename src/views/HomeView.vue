<template>
  <main class="flex justify-center items-center columns pa-20" style="height: 100%">
    <h1 v-if="firstGif">Est ce que tu m'aimes ?</h1>
    <h1 v-else>Moi aussi je t'aime !</h1>

    <img v-if="firstGif" src="../assets/giphy.webp" alt="giphy" class="gif-size" />
    <img v-else src="../assets/metoo.webp" alt="giphy" class="gif-size" />

    <section class="flex gap-10 mt-20">
      <button v-if="firstGif" @mouseenter="move" @click="move" :style="positionNo" class="button-custom no-love">
        Non
      </button>
      <button @click="yes" class="button-custom love">Oui</button>
    </section>
  </main>
</template>

<script setup>
import { ref } from 'vue'

const firstGif = ref(true)

const positionNo = ref({
  position: 'unset',
  top: '0',
  left: '0',
})

const move = () => {
  positionNo.value = {
    position: 'absolute',
    top: `${Math.floor(Math.random() * 50)}%`,
    left: `${Math.floor(Math.random() * 50)}%`,
  }
}

const yes = () => {
  firstGif.value = !firstGif.value
}
</script>
