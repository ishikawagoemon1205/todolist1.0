<script>
export default {
  data() {
    return {
      newTask: "",
      tasks: [],
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== "") {
        this.tasks.push(this.newTask.trim());
        this.newTask = "";
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<template>
  <div>
    <header>
      <div class="header-title">
        <h1>To Do List</h1>
      </div>
    </header>
    <body>
      <h3 class="todo-register-title">To Do 登録</h3>
      <div class="input-zone">
        <div class="input-zone-box">
          <input
            type="text"
            v-model="newTask"
            class="input-zone-box-value"
            placeholder="文字を入力してください。"
          >
        </div>
        <div class="input-zone-box">
          <button type="button" @click="addTask" class="input-zone-box-button">登録！</button>
        </div>
      </div>
      <h3 class="todo-register-title">To Do List</h3>
      <div class="todo-list">
        <div class="todo-list-check-button"></div>
        <div class="todo-list-check-task">
          <div v-for="(task, index) in tasks" :key="index" class="task-item-container">
           <div class="task-item">{{ task }}</div>
           <button @click="removeTask(index)" class="remove-button">完了</button>
          </div>
        </div>
      </div>
    </body>
  </div>
</template>

<style>
html {
  background-color: #F5F5F7;
}

header {
  width: 100%;
  height: 120px;
  background-color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
}
.todo-register-title {
  display: flex;
  justify-content: center;
  padding-top: 32px;
  padding-bottom: 16px;
  border-bottom: 2px solid #A6A6A6;
  margin-left:100px;
  margin-right:100px;
}
.input-zone {
  display: flex;
  justify-content: center;
  height: 300px;
  margin:0 100px 0 100px;
}
.input-zone-box {
  flex: 1;
  display: flex;
  justify-content: center;
}
.input-zone-box-value {
  width: 80%;
  height: 80%;
  margin-top: 24px;
  background-color: #fff;
  border-radius: 20px;
  border:2px solid #fff;
  font-size: 24px;
  padding: 10px;
}
.input-zone-box-button{
  width: 80%;
  height: 80px;
  margin-top: 100px;
  background-color: #fff;
  border-radius: 50px;
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3);
  border:2px solid #fff;
  font-size: 30px;
}
.input-zone-box-value::placeholder {
  font-size: 14px;
}
.todo-list {
  height: 140px;
  margin-top: 50px;
  margin-left: 100px;
  margin-right: 100px;
  display: flex;

}
.task-item {
  widows: 100px;
  margin: 10px;
  padding: 10px;
  font-size: 24px;
  background-color: #fff;
  border-radius: 50px;
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3);
}
.task-item-container {
  display: flex;
  align-items: center;
}
.remove-button {
  width: 50px;
  height: 50px;
  border-radius: 50px;
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3);
  background-color: #fff;
  border-color: #FFF;
}
</style>