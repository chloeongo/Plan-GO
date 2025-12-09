<script>
import Header from './components/header.vue'
import List from './components/list.vue'
import Background from './components/background.vue'

import { ref } from 'vue'
import defaultBg from './assets/background.png'

export default {
  components: { Header, List, Background },
  setup() {
    const background = ref(defaultBg)

    const updateBackground = (newBg) => {
      background.value = newBg
    }

    return { background, updateBackground }
  },
}
</script>

<template>
  <div :style="{ backgroundImage: `url(${background})` }" class="appBg">
    <Header @change-bg="updateBackground" />
    <List class="listComp" />
    <Background @change-bg="updateBackground" />
  </div>
</template>

<style scoped>
.listComp {
  position: relative;
  z-index: 10;
}

.appBg {
  background-repeat: no-repeat;
  background-size: cover;
  width: 100%;
  height: 100vh;
  margin: 0px;
}
</style>
