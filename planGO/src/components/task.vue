<script>
export default {
  data() {
    return {
      tasks: [],
      name: null,
      desc: null,
      newName: '',
      newDesc: '',
      editTask: false,
      addTask: false,
    }
  },
  methods: {
    saveTask() {
      if (!this.newName.trim()) {
        alert('Task name is required')
        return
      }
      this.tasks.push({
        id: Date.now(),
        name: this.newName,
        desc: this.newDesc || '',
      })
      this.newName = ''
      this.newDesc = ''
      this.addTask = false
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id)
      this.editTask = false
    },
  },
}
</script>

<template>
  <div>
    <div class="task" v-for="task in tasks" :key="task.id">
      <!--Taak display-->
      <div class="taskHeading">
        <p style="font-weight: 500; font-size: 15px">{{ task.name }}</p>
        <p class="closeTask" @click="editTask = !editTask">...</p>
      </div>
      <p style="font-size: 12px; margin-top: -10px">{{ task.desc }}</p>

      <!--Bewerk lijst-->
      <div class="actionList" v-if="editTask">
        <div class="actionsTitle">
          <p style="font-weight: 500; margin-left: 10px">Task actions</p>
        </div>
        <div class="listActions">
          <div>
            <p>Edit task</p>
          </div>
          <div @click="deleteTask(task.id)">
            <p style="color: red">Delete this task</p>
          </div>
        </div>
      </div>
    </div>

    <!--Taak input velden-->
    <div class="taskInput" v-if="addTask">
      <form @submit.prevent="saveTask">
        <input type="text" v-model="newName" placeholder="Type a task name..." required />
        <input type="text" v-model="newDesc" placeholder="Type a description..." />

        <button type="submit">Save</button>
      </form>
    </div>

    <!--Voeg een nieuwe taak-->
    <div class="addList" id="addTask">
      <button @click="addTask = !addTask">+</button>
      <p style="margin-left: 20px">Add task</p>
    </div>
  </div>
</template>

<style>
.listActions div:hover {
  background-color: #f1f1f1;
  cursor: pointer;
}

.listActions {
  display: grid;
  grid-template-rows: auto;
  gap: 5px;
}

.listActions div {
  padding-left: 10px;
  transition: all 0.7s;
  border-radius: 15px;
  border: 1px solid #eaeaea;
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
