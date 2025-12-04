<script>
export default {
  data() {
    return {
      showMenu: true,
    }
  },
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
        <div><img src="../assets/background.png" /></div>
        <div><img src="../assets/background-2.jpg" /></div>
        <div><img src="../assets/background-3.jpg" /></div>
        <div><img src="../assets/background-4.jpg" /></div>
        <div><img src="../assets/background-5.jpg" /></div>
        <div><img src="../assets/background-6.jpg" /></div>
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
