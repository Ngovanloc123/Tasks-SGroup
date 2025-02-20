<script setup>
import { reactive, ref } from "vue";
import { v4 as uuidv4 } from "uuid";

const props = defineProps({
  handleShowTaskDetail: Function,
});

const todoDetail = reactive({
  id: "",
  subject: "",
  title: "",
  description: "",
  date: "",
  status: 0,
});

function getData() {
  if (
    todoDetail.subject == "" ||
    todoDetail.title == "" ||
    todoDetail.description == ""
  ) {
    alert("Nhập đầy đủ vào!!!");
    return;
  }
  console.log(todoDetail);
}
</script>

<template>
  <div class="overlay"></div>

  <div class="container">
    <div class="content">
      <button class="ti-close" @click="handleShowTaskDetail(false)"></button>
      <h1 class="title-content">Edit todo</h1>
      <div class="inputs">
        <input
          class="subject"
          type="text"
          placeholder="Subject"
          v-model="todoDetail.subject"
        />
        <input
          class="title"
          type="text"
          placeholder="Title"
          v-model="todoDetail.title"
        />
        <textarea
          class="description"
          placeholder="Description"
          v-model="todoDetail.description"
        ></textarea>
      </div>
      <div class="buttons">
        <div>
          <input
            v-model="todoDetail.status"
            type="radio"
            name="tick"
            value="0"
          />
          <label for="">To do</label>
        </div>
        <div>
          <input
            v-model="todoDetail.status"
            type="radio"
            name="tick"
            value="1"
          />
          <label for="">Doing </label>
        </div>
        <div>
          <input
            v-model="todoDetail.status"
            type="radio"
            name="tick"
            value="2"
          />
          <label for="">Finished</label>
        </div>
      </div>
      <button class="submit" @click.prevent="getData()">Submit</button>
    </div>
  </div>
</template>

<style scoped>
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 2;
  transition: opacity 0.5s ease-in-out;
}

.ti-close {
  color: #000;

  cursor: pointer;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  height: 100vh;
  z-index: 3;
}

.content {
  position: absolute;

  background-color: #fff;
  border-radius: 10px;
  padding: 20px;
  margin: 20px auto;
  width: 600px;
  height: 300px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.title-content {
  text-align: center;
  color: rgb(127, 120, 112);
}

.inputs {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-bottom: 20px;
  gap: 10px;
}

.inputs input {
  padding: 10px;
  border: none;

  box-shadow: 1px 2px 2px rgba(0, 0, 0, 0.23);
}

.inputs textarea {
  padding: 10px;
  border: none;

  box-shadow: 1px 2px 2px rgba(0, 0, 0, 0.23);
  resize: vertical;
}

.buttons {
  display: flex;
  justify-content: space-around;
  gap: 10px;
}

.buttons label {
  color: #6f5555;
  font-size: 1.5rem;
}

.submit {
  margin-top: 10px;
  width: 100%;
  padding: 10px 20px;
  background-color: #527389;
  color: #fff;
  border: none;
  cursor: pointer;
  font-size: 1.2rem;
  border-radius: 5px;
}
</style>
