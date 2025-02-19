<script setup>
defineProps({
  msg: {
    subject: String,
    title: String,
    description: String,
    date: String,
  },
})
</script>

<template>
  <div class="container">
    <div class="content">
      <div class="header">
        <a href="" class="subject">{{ subject }}</a>
      </div>
      <h2 class="title">{{ title }}</h2>
      <div class="break"></div>
      <p class="description">{{ description }}</p>
      <div class="time">
        <i class="ti-alarm-clock"></i>
        <div class="date">{{ date }}</div>
      </div>
    </div>
    <div class="btn-header">
      <button class="ti-eraser"></button>
      <button class="ti-trash"></button>
    </div>
  </div>
</template>

<style scoped>

template {
    
}
.container {
  display: flex;
  justify-content: space-between;
  align-items: start;
  width: 100%;
  /* height: 50px; */
  padding: 20px 30px;
  background-color: #fff;
  border: 1px solid #706d6d;
  border-radius: 8px;
}
.content {
  width: 70%;
  height: 150px;
}

.header {
}

.subject {
  color: #4d76e4;
}

.btn-header {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  margin-top: 10px;
}

.btn-header button {
  border: none;
  background-color: transparent;
  color: #000;
  font-size: 24px;
  cursor: pointer;
  transition: .3s ease;
}
.btn-header button:hover {
    color: #fff;
    background: #928d8d;
    border-radius: 5px;
}

.title {
  color: #000;
  font-size: 1rem;
  font-weight: bold;
}

.break {
  margin-bottom: 20px;
  border-bottom: 2px solid #ccc;
}

.description {
  font-size: 0.8rem;
  margin-top: -10px;
  color: #666;
}

.time {
  color: #666;
  display: flex;
}
</style>
