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
      })
    },
  },
}
</script>

<template>
  <div class="main">
    <div v-for="list in lists" :key="list.id" class="list">

      <div class="title">
        <h4>{{ list.title }}</h4>
        <p style="font-size: 28px; font-weight: 500;">...</p>
      </div>

      <!--Input veld naam bewerken-->
      <div class="listForm">
        <form>
            <input type="text" :value="list.title"></input>
            <button type="submit">Save</button>
        </form>
      </div>

      <div class="addList">
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
    transition: all 1s;
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
  transition: all 1s;
  height: 100%;
  min-width: 65px;
  max-height: 65px;
}

.addList button:hover {
  color: #ffcc00;
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
</style>
