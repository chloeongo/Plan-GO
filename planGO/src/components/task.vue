<script>
export default {
  data() {
    return {
      addTask: false,
      name: 'Task name',
      desc: 'desc',
    }
  },
  methods: {},
}
</script>

<template>
  <div>
    <!--Taak input velden-->
    <div class="taskInput" v-if="addTask">
      <form>
        <input type="text" placeholder="Type a task name..." />
        <button type="submit">Save</button>
      </form>
    </div>

    <!--Taak display-->
    <div class="task">
      <div class="taskHeading">
        <p style="font-weight: 500; font-size: 15px">{{ name }}</p>
        <p class="closeTask">...</p>
      </div>
      <p style="font-size: 12px; margin-top: -10px">{{ desc }}</p>
    </div>

    <!--Voeg een nieuwe taak-->
    <div class="addList" id="addTask">
      <button @click="addTask = !addTask">+</button>
      <p style="margin-left: 20px">Add task</p>
    </div>
  </div>
</template>

<style>
.closeTask {
  font-size: 20px;
  font-weight: 500;
  transition: all 0.2s;
  margin-top: 0px;
}

.closeTask:hover {
  color: #ffcc00;
  cursor: pointer;
}

.taskInput {
  background-color: #fff;
  padding: 10px;
  border: 1px solid #eaeaea;
  border-radius: 15px;
}

input {
  background-color: #fff;
  border: none;
  border-radius: 15px;
  padding: 12px;
  width: 90%;
  border: 1px solid #eaeaea;
}

form button:hover {
  background-color: #06aacb;
}

form button {
  background-color: #00c0e8;
  color: #fff;
  padding: 12px;
  border-radius: 15px;
  width: 100%;
  border: none;
  margin-top: 10px;
  transition: all 0.5s;
}

.task {
  background-color: #fff;
  padding: 10px;
  width: 92%;
  border-radius: 15px;
  border: 1px solid #eaeaea;
}

.taskHeading {
  display: flex;
  width: 100%;
  justify-content: space-between;
  margin-top: -5px;
}

.addList {
  background-color: #f1f1f1;
  display: flex;
  align-items: center;
  border-radius: 20px;
  width: 280px;
  transition: all 1s;
  color: #00c0e8;
  height: 65px;
  border: 1px solid #eaeaea;
}

.addList:hover {
  background-color: #fff;
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
  display: flex;
  align-items: center;
}

.addList button:hover {
  color: #ffcc00;
  background-color: #fff;
}

#addTask {
  background-color: #fff;
  margin-top: 15px;
}

#addTask button {
  background-color: #fff;
}
</style>
