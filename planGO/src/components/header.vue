<script>
import Background from './background.vue'

export default {
  components: {
    Background,
  },
  data() {
    return {
      showMenu: false,
    }
  },
}
</script>

<template>
  <header>
    <div><img src="../assets/logo.png" /></div>
    <div></div>
    <div class="btns">
      <img src="../assets/image.png" @click="showMenu = !showMenu" />
      <a href="https://github.com/chloeongo" target="_blank">
        <img src="../assets/github-logo.png" />
      </a>
    </div>
  </header>

  <Background v-if="showMenu" />
</template>

<style scoped>
header {
  width: 97%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
}

img:hover {
  cursor: pointer;
}

.btns img {
  width: 45px;
}
</style>
