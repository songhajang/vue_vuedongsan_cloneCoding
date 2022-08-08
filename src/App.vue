<template>
  <div>
    <!-- 메뉴바 -->
    <div class="menu">
      <!-- <a v-for="menuLi in 3" :key="menuLi">HOME</a> -->

      <a v-for="(menuLi, idx) in menu" :key="idx">{{menuLi}}</a>

    </div>

    <h1>{{logo}}</h1>

    <div>
      <h4>{{products[0]}}</h4>
      <p>{{price[0]}} 만원</p>
      <button 
        @click="increase(0)">
        허위매물신고</button> <span>신고수 : {{신고수[0]}}</span>
    </div>
    <div>
      <h4>{{products[1]}}</h4>
      <p>{{price[1]}} 만원</p>
      <button 
        @click="increase(1)">
        허위매물신고</button> <span>신고수 : {{신고수[1]}}</span>
    </div>
    <div>
      <h4>{{products[2]}}</h4>
      <p>{{price[2]}} 만원</p>
      <button 
        @click="increase(2)">
        허위매물신고</button> <span>신고수 : {{신고수[2]}}</span>
    </div>

  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
        logo : '원룸샵',
        menu : ['Home', 'Shop', 'About'],
        products : ['역삼동원룸','청호동원룸','마포구원룸'],
        price : [60,70,80],
        신고수 : [0,0,0],
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
</style>
