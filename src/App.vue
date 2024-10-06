<template>
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>

  <img alt="Vue logo" src="./logo.png" @click="imgClcked = true" />
  <div v-if="imgClcked === true">이미지 눌렀다</div>

  <div v-for="(room, i) in onerooms" :key="i">
    <h4>{{ room.name }}</h4>
    <p :style="style">{{ room.price }} 만원</p>
    <button @click="handleReport(i)">허위매물신고</button>
    <span @mouseover="handleAlert()">신고수:{{ room.report }}</span>
  </div>
</template>

<script>
import roomData from "./roomData";

export default {
  name: "App",
  data() {
    return {
      imgClcked: false,
      style: "color: blue",
      menus: ["Home", "Product", "About"],
      onerooms: roomData,
    };
  },
  methods: {
    handleReport(i) {
      this.onerooms[i].report++;
    },
    handleAlert() {
      alert("fucufuc");
    },
  },
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>
