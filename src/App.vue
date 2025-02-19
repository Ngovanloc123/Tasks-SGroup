<script setup>
  import task from "./components/task.vue";
  import { ref } from "vue";

  const tasks_todo = ref([]);

  const addTask_todo = () => {
    tasks_todo.value.push({
      subject: "Marketing",
      title: "Write SEO article for new product",
      description:
        "This is an existential moment for effective altruism and the rationalist community writ-large",
      date: new Date().toLocaleDateString(),
    });
  };
</script>

<template>
  <div class="container">
    <div class="header">
      <div class="logo">
        <img src="./assets/images/logo.png" alt="" class="logo-img" />
        <p class="logo-text">
          Let's get shit done!
          <img src="./assets/images/hi.png" alt="" class="text-img" />
        </p>
      </div>
      <button class="task-btn" @click="addTask_todo">
        <i class="ti-plus"></i>New task
      </button>
    </div>

    <!-- ================= CONTENT =================== -->
    <div class="content">
      <ul class="task-list">
        <!-- ============= LIST TODO ================ -->
        <li class="list-todo item-list">
          <div class="col">
            <h3 class="title">Todo</h3>
            <p class="count-task">{{ tasks_todo.length }}</p>
          </div>
          <ul class="tasks">
            <task v-for="task in tasks_todo" :key="task.title" :msg="task" />
          </ul>
        </li>
        <!-- ============= LIST DOING ============== -->
        <li class="list-doing item-list">
          <div class="col">
            <h3 class="title">Doing</h3>
            <p class="count-task">1</p>
          </div>
          <ul class="tasks">
            <task />
          </ul>
        </li>
        <!-- ============ LIST FINISHED ============= -->
        <li class="list-finished item-list">
          <div class="col">
            <h3 class="title">Finished</h3>
            <p class="count-task">1</p>
          </div>
          <ul class="tasks">
            <task />
          </ul>
        </li>

      </ul>
    </div>
  </div>
</template>

<style scoped>
.container {
  width: 90%;
  margin: auto;
  margin-bottom: 12px;
  /* box-sizing: border-box; */
}
.header {
  display: flex;
  justify-content: space-between;
  align-items: end;
  padding: 20px;
}

.logo .logo-img {
  width: 160px;
}
.logo-text {
  font-size: 1rem;
  font-weight: 200;
  margin-left: 10px;
}

.logo-text .text-img {
  width: 36px;
  margin-top: -20px;
}

.ti-plus {
  margin-right: 8px;
}

.task-btn {
  color: #757171;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.task-btn:hover {
  color: #fff;
  background-color: #433f3f;
}

/* ============== CONTENT ============= */
.content {
}

.task-list {
  width: 100%;
  list-style: none;
  display: flex;
  justify-content: space-between;
  align-items: center;
  /* padding: 20px; */
  margin-top: -10px;
  margin-left: -30px;
}

.item-list {
  width: 30%;
  height: 40px;
  color: #fff;
  padding: 0px 8px;
  border-radius: 8px;
}

.col {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-bottom: 20px;
}

.list-todo,
.list-todo::after {
  background-color: #05a5d9;
}

.list-todo .count-task {
  background: #09cadd;
}

.list-doing,
.list-doing::after {
  background: #e3cf86;
}

.list-doing .count-task {
  background: #d8b600;
}

.list-finished,
.list-finished::after {
  background: #3cc057;
}

.list-finished .count-task {
  background: #6dcf79;
}

.item-list {
  position: relative;
}

.item-list::after {
  content: "";
  position: absolute;
  bottom: -22px;
  left: 50%;
  transform: translateX(-50%);
  width: 100%;
  height: 2px;
  /* background-color: #757171; */
}

.title {
  font-size: 1.2rem;
  font-weight: 500;
  margin-top: 8px;
}

.count-task {
  width: 20px;
  height: 20px;
  text-align: center;
  margin-top: 8px;
}

.tasks {
  list-style: none;
  width: 100%;
  margin-left: -50px;
}
</style>
