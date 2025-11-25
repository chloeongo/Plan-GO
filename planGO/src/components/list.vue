<script>
export default {
  data() {
    return {
      lists: [],
    }
  },
  methods: {
    addList() {
      this.lists.push({
        id: Date.now(),
        title: 'Hello World!',
        important: false,
        editList: false,
        changeName: false,
      })
    },
  },
}
</script>

<template>
  <div class="main">
    <div v-for="list in lists" :key="list.id" class="list" :class="{ important: list.important }">

    <div class="heading"> 
      <div class="title">
        <h4 @click="list.changeName = !list.changeName">{{ list.title }}</h4>
        <p style="font-size: 28px; font-weight: 500;" 
        @click="list.editList = !list.editList">
        ...
        </p>
      </div>
      
      <!--Bewerk lijst-->
      <div class="actionList" v-if="list.editList">
        <div class="actionsTitle">
            <p style="font-weight: 500; margin-left: 10px;">Edit list</p>
        </div>
        <div class="listActions">
            <div @click="list.important = !list.important">
                <p>Mark as important</p>
            </div>
            <div>
                <p style="color: red;">Delete this list</p>
            </div>
        </div>
      </div>
    </div>   

      <!--Input veld naam bewerken-->
      <div class="listForm" v-if="list.changeName">
        <form>
            <input type="text" :value="list.title"></input>
            <button type="submit">Save</button>
        </form>
      </div>

    <!--Voeg een nieuwe taak-->
      <div class="addList" id="addTask">
        <button @click="addList">+</button>
        <p>Add task</p>
      </div>

    </div>

    <div class="addList">
      <button @click="addList">+</button>
      <p>Create new list</p>
    </div>

  </div>
</template>

<style scoped>
button{
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
}

button:hover{
    cursor: pointer;
}

p,
button,
h4 {
  color: #000;
}

input{
    background-color: #fff;
    border: none;
    border-radius: 15px;
    padding: 12px;
    width: 92%;
}

form button{
    background-color: #00c0e8;
    color: #fff;
    padding: 12px;
    border-radius: 15px;
    width: 100%;
    border: none;
    margin-top: 10px;
    transition: all 0.5s;
}

.important{
    background-color: #FF383C !important;
}

.heading{
    width: 100%;
}

#addTask{
    background-color: #fff;
    margin-top: 15px;
}

form button:hover{
    background-color: #06aacb;
}

.title{
    width: 100%;
    display: flex;
    justify-content: space-between;
}

.title p{
    margin-top: 0px;
    transition: all 0.5s;
}

.title p:hover{
    cursor: pointer;
    color: #ffcc00;
}

.listForm{
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

#addTask button{
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

.addList:hover{
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

.actionList{
    position: absolute;
    background-color: #fff;
    padding: 10px;
    border-radius: 15px;
    width: 200px;
    margin-left: 250px;
    margin-top: -20px;
    z-index: 3;
}

.listActions{
    display: grid;
    grid-template-rows: auto;
    gap: 10px;
}

.listActions div:hover{
    background-color: #f1f1f1;
    cursor: pointer;
}

.listActions div{
    padding-left: 10px;
    transition: all 0.7s;
    border-radius: 15px;
}
</style>
