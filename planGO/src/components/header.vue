<script setup>
import { ref } from 'vue'
import { defineEmits } from 'vue'
import Background from './background.vue'

const showMenu = ref(false)

const emit = defineEmits(['change-bg'])

const updateBackground = (newBg) => {
  emit('change-bg', newBg)
}
</script>

<template>
  <header>
    <div class="headerContent">
      <div><img src="../assets/logo.png" /></div>
      <div></div>
      <div class="btns">
        <img src="../assets/image.png" @click="showMenu = !showMenu" />
        <a href="https://github.com/chloeongo" target="_blank">
          <img src="../assets/github-logo.png" />
        </a>
      </div>
    </div>
  </header>

  <Background v-if="showMenu" @change-bg="updateBackground" />
</template>

<style scoped>
header {
  width: 97%;
  padding-bottom: 80px;
}

.headerContent {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
}

header .headerContent {
  position: fixed;
  width: 97%;
}

img:hover {
  cursor: pointer;
}

.btns img {
  width: 45px;
}
</style>
