<template>
      <div class="black-bg" v-if="modal == true">
      <div class="white-bg">
        <img :src="datas[useClick].image" alt="" style="width: 100%">
        <h4>{{datas[useClick].title}}</h4>
        <p>{{datas[useClick].content}}</p>
        <p>{{datas[useClick].price}} 원</p>
        <!-- <button @click="modal = false">닫기</button> -->
      </div>
    </div>
</template>

<script>
export default {
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