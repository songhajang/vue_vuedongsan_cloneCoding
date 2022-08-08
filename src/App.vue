<template>
  <div>
    <!-- 메뉴바 -->
    <div class="menu">
      <!-- <a v-for="menuLi in 3" :key="menuLi">HOME</a> -->
      <a v-for="(menuLi, idx) in menu" :key="idx">{{menuLi}}</a>
    </div>

    <main-discount />

    <details-modal :datas="datas" :useClick="useClick" :modal="modal"/>

    <div v-for="(data, key) in datas" :key="key">
      <img :src="data.image" class="room-img">
      <h4 @click="modal = true; useClick = key ">{{data.title}}</h4>
      <p>{{data.price}} 원</p>
    </div>

  </div>
</template>

<script>

import  dataList from './components/oneroom.js';
import MainDiscount from './components/MainDiscount.vue';
import DetailsModal from './components/DetailsModal.vue';

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
    MainDiscount,
    DetailsModal,
}
}
</script>

<style>
*{
  cursor: pointer;
}
body{
  margin: 0;
  text-align: center;
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
