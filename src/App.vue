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

    <main-discount v-if="sale === true" :Val="amount"/>

    <button @click="priceMinSort">가격순 정렬</button>
    <button @click="priceMaxSort">역가격순 정렬</button>
    <button @click="ABCSort">가나다순 정렬</button>
    <button @click="sortBack">되돌리기</button>


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
        originDatas : [...dataList],
        datas : dataList,
        modal : false,
        menu : ['Home', 'Shop', 'About'],
        신고수 : [0,0,0],
        useClick : 0,
        sale : true,
        amount : 20
    }
  },
  methods: {
    increase(e){
      this.신고수[e] += 1;
    },
    priceMinSort(){
      this.datas.sort(function(a,b){
        return a.price - b.price
      })
    },
    
    priceMaxSort(){
      this.datas.sort(function(a,b){
        return b.price - a.price 
      })
    },

    ABCSort(){
      let arr = []
      let datas = this.datas
      datas.forEach( data => {
        arr.push(data.title.split('')[0])
      });
      arr = arr.sort()
      this.datas.sort(function(a){
        console.log(arr)
        arr.forEach(e =>{
          console.log(e)
          if(a.title.findIndex(e) == true){
            return a.title
          }
        })
      })

      // this.datas.sort(function(a){
        
      // })
    },
    sortBack(){
      this.datas = [...this.originDatas]
    },
  },
  components: {
    MainDiscount,
    DetailsModal,
    RoomList,
},
mounted(){
  const a = setInterval(()=>{
    console.log(this.amount --)
    if( this.amount < 0){
      setTimeout(()=>{
        this.sale = false
        stop()
      })
    }
  },1000);

    function stop(){
      console.log('stop')
      clearInterval(a)
    }
},
update(){
  
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
