<template>
  <div>
    <!-- 메뉴바 -->
    <div class="menu">
      <!-- <a v-for="menuLi in 3" :key="menuLi">HOME</a> -->

      <a v-for="(menuLi, idx) in menu" :key="idx">{{menuLi}}</a>

    </div>

    <div class="black-bg" v-if="modal == true">
      <div class="white-bg">
        <img :src="datas[useClick].image" alt="">
        <h4>{{datas[useClick].title}}</h4>
        <p>{{datas[useClick].content}}</p>
        <p>{{datas[useClick].price}} 원</p>
        <button @click="modal = false">닫기</button>
      </div>
    </div>

    <div v-for="(data, key) in datas" :key="key">
      <img :src="data.image" class="room-img">
      <h4 @click="modal = true; useClick = key ">{{data.title}}</h4>
      <p>{{data.price}} 원</p>
    </div>

  </div>
</template>

<script>

import  dataList from './components/oneroom.js';

export default {
  name: 'App',
  data() {
    return {
        datas : dataList,
        modal : false,
        menu : ['Home', 'Shop', 'About'],
        신고수 : [0,0,0],
        useClick : 0,
    }
  },
  methods: {
    increase(e){
      this.신고수[e] += 1;
    },
  },
  components: {
  }
}
</script>

<style>
*{
  cursor: pointer;
}
body{
  margin: 0;
}
div{
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  top: 0;
  padding: 20px;
}
.white-bg{
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color : white;
  padding: 10px;
}
.room-img{
  width: 100%;
  margin-top: 40px;
}
</style>
