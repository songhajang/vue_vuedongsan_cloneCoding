<template>
  <div>

    <transition name="fade">
      <details-modal @ColseModal="modal = false" :datas="datas" :useClick="useClick" :modal="modal"/>
    </transition>

    <!-- 메뉴바 -->
    <div class="menu">
      <!-- <a v-for="menuLi in 3" :key="menuLi">HOME</a> -->
      <a v-for="(menuLi, idx) in menu" :key="idx">{{menuLi}}</a>
    </div>

    <main-discount />


    <room-list @openModal="modal = true; useClick = $event"  :datas="datas[key]" v-for="(data, key) in datas" :key="key"/>


  </div>
</template>

<script>

import  dataList from './components/oneroom.js';
import MainDiscount from './components/MainDiscount.vue';
import DetailsModal from './components/DetailsModal.vue';
import RoomList from './components/OneRoomCard.vue' ;

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
    RoomList,
}
}
</script>

<style>
.fade-enter-from{ opacity: 0; }
.fade-enter-active{ transition: all 0.5s; }
.fade-enter-to{ opacity: 1; }
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
</style>
