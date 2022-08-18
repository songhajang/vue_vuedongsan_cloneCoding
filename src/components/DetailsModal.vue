<template>
      <div class="black-bg" v-if="modal == true">
      <div class="white-bg">
        <img :src="datas[useClick].image" alt="" style="width: 100%">
        <h4>{{datas[useClick].title}}</h4>
        <p>{{datas[useClick].content}}</p>
        <input v-model="month">
        <p>{{month}}개월 / {{datas[useClick].price * month}} 원</p>
        <button @click="$emit('ColseModal')">닫기</button>
      </div>
    </div>
</template>

<script>
export default {
  data(){
    return{
      month : 1,
    }
  },
  watch :{
    month(value){
      if(isNaN(value) == true){
        alert('문자 입력 안됩니다~')
        this.month = 1
      }
    }
  },
    props:{
      modal : Boolean,
      datas : Object,
      useClick: Number,

    }
}
</script>

<style>
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
</style>