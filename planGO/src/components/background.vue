<script setup>
import { ref } from 'vue'
import { defineEmits } from 'vue'

import bg1 from '../assets/background.png'
import bg2 from '../assets/background-2.jpg'
import bg3 from '../assets/background-3.jpg'
import bg4 from '../assets/background-4.jpg'
import bg5 from '../assets/background-5.jpg'
import bg6 from '../assets/background-6.jpg'

const showMenu = ref(true)

const emit = defineEmits(['change-bg'])

const selectBg = (img) => {
  emit('change-bg', img)
}
</script>

<template>
  <div class="mainBg">
    <div class="container" v-if="showMenu">
      <div class="menuTop">
        <h3>Change background image</h3>
        <p @click="showMenu = !showMenu">✖</p>
      </div>
      <div class="gallery">
        <div>
          <img @click="selectBg(bg1)" :src="bg1" />
        </div>
        <div>
          <img @click="selectBg(bg2)" :src="bg2" />
        </div>
        <div>
          <img @click="selectBg(bg3)" :src="bg3" />
        </div>
        <div>
          <img @click="selectBg(bg4)" :src="bg4" />
        </div>
        <div>
          <img @click="selectBg(bg5)" :src="bg5" />
        </div>
        <div>
          <img @click="selectBg(bg6)" :src="bg6" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.menuTop {
  width: 100%;
  display: flex;
  justify-content: space-between;
}

.menuTop p:hover {
  cursor: pointer !important;
}

.mainBg {
  width: 100%;
  height: 70vh;
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
}

.container {
  padding: 20px;
  border-radius: 15px;
  background-color: #fff;
  border: 1px solid #eaeaea;
  width: 600px;
  height: 360px;
  position: absolute !important;
  z-index: 10;
}

.gallery {
  display: grid;
  grid-template-rows: 1fr 1fr;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 10px;
}

img {
  width: 100%;
  height: 100%;
  background-repeat: no-repeat;
  border-radius: 10px;
}

.gallery img:hover {
  cursor: pointer;
  border: 2px solid #ff383c;
}
</style>
