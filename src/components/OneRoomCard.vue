<template>
    <div>
        <img :src="datas.image" class="room-img">
        <h4 @click="modal = true; useClick = key ">{{datas.title}}</h4>
        <p>{{datas.price}} 원</p>
    </div>
</template>

<script>
export default {
    props:{
        datas : Object,
    }
}
</script>

<style>
.room-img{
  width: 100%;
  margin-top: 40px;
}
</style>