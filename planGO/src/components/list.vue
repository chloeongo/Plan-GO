<script>
import Task from './task.vue'

export default {
  components: {
    Task,
  },
  data() {
    return {
      lists: [],
    }
  },
  methods: {
    addList() {
      this.lists.push({
        id: Date.now(),
        title: null,
        newTitle: '', // Placeholder, zodat title niet meteen wordt geupdate
        important: false,
        editList: false,
        changeName: false,
      })
    },
    deleteList(id) {
      this.lists = this.lists.filter((list) => list.id !== id)
    },
    saveTitle(list) {
      if (!list.newTitle) {
        alert('List name cannot be empty')
        return
      }
      list.title = list.newTitle
      list.changeName = false
      list.newTitle = ''
    },
  },
}
</script>

<template>
  <div class="main">
    <div v-for="list in lists" :key="list.id" class="list" :class="{ important: list.important }">
      <div class="heading">
        <!--Heading-->
        <div class="title">
          <h4 @click="list.changeName = !list.changeName">{{ list.title }}</h4>
          <p style="font-size: 28px; font-weight: 500" @click="list.editList = !list.editList">
            ...
          </p>
        </div>

        <!--Bewerk lijst-->
        <div class="actionList" v-if="list.editList">
          <div class="actionsTitle">
            <p style="font-weight: 500; margin-left: 10px">List actions</p>
          </div>
          <div class="listActions">
            <div @click="list.important = !list.important">
              <p>Mark as important</p>
            </div>
            <div @click="list.changeName = !list.changeName">
              <p>Edit list name</p>
            </div>
            <div @click="deleteList(list.id)">
              <p style="color: red">Delete this list</p>
            </div>
          </div>
        </div>
      </div>

      <!--Input veld naam bewerken-->
      <div class="listForm" id="editForm" v-if="list.changeName || !list.title">
        <form @submit.prevent="saveTitle(list)">
          <input type="text" v-model="list.newTitle" :placeholder="list.title" />
          <button type="submit" class="blueBtn">Save</button>
        </form>
      </div>

      <!--Voeg een nieuwe taak-->
      <Task v-if="list.title" />
    </div>

    <div class="addList">
      <button @click="addList">+</button>
      <p>Create new list</p>
    </div>
  </div>
</template>

<style scoped>
button {
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
}

button:hover {
  cursor: pointer;
}

p,
button,
h4 {
  color: #000;
}

#editForm {
  margin-bottom: 15px;
}

input {
  background-color: #fff;
  border: none;
  border-radius: 15px;
  padding: 12px;
  width: 92%;
  border: 1px solid #eaeaea;
}

.blueBtn {
  background-color: #00c0e8;
  color: #fff;
  padding: 12px;
  border-radius: 15px;
  width: 100%;
  border: none;
  margin-top: 10px;
  transition: all 0.5s;
}

.important {
  background-color: #ff383c !important;
}

.heading {
  width: 100%;
}

#addTask {
  background-color: #fff;
  margin-top: 15px;
}

.blueBtn:hover {
  background-color: #06aacb;
}

.title {
  width: 100%;
  display: flex;
  justify-content: space-between;
}

.title p {
  margin-top: 0px;
  transition: all 0.5s;
}

.title p:hover {
  cursor: pointer;
  color: #ffcc00;
}

.listForm {
  width: 100%;
  display: grid;
  grid-template-columns: auto;
}

.addList button {
  color: #00c0e8;
  border: none;
  background-color: #f1f1f1;
  font-size: 24px;
  padding: 20px;
  border-radius: 20px;
  transition: all 0.5s;
  height: 100%;
  min-width: 65px;
  max-height: 65px;
}

.addList button:hover {
  color: #ffcc00;
  background-color: #fff;
}

#addTask button {
  background-color: #fff;
}

.main {
  display: grid;
  grid-auto-flow: column;
  grid-auto-columns: 300px;
  align-items: start;
  gap: 50px;
  padding: 20px;
}

.addList {
  background-color: #f1f1f1;
  display: flex;
  align-items: center;
  border-radius: 20px;
  width: 300px;
  transition: all 1s;
}

.addList:hover {
  background-color: #fff;
}

.list {
  width: 280px;
  padding-bottom: 20px;
  background-color: #f1f1f1;
  display: flex;
  align-items: center;
  border-radius: 20px;
  display: flex;
  flex-wrap: wrap;
}

.list {
  margin-right: 60px;
  padding-left: 20px;
  padding-right: 20px;
}
.addList {
  gap: 20px;
  padding-right: 20px;
}

.addList p {
  color: #00c0e8;
}

.actionList {
  position: absolute;
  background-color: #fff;
  padding: 10px;
  border-radius: 15px;
  width: 200px;
  margin-left: 250px;
  margin-top: -20px;
  z-index: 3;
  border: 1px solid #eaeaea;
}

.listActions {
  display: grid;
  grid-template-rows: auto;
  gap: 5px;
}

.listActions div:hover {
  background-color: #f1f1f1;
  cursor: pointer;
}

.listActions div {
  padding-left: 10px;
  transition: all 0.7s;
  border-radius: 15px;
  border: 1px solid #eaeaea;
}
</style>
