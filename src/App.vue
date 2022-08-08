<template>
  <div>
    <img src="./assets/logo.png" alt="">
    <h1>{{logo}}</h1>
    <div>
      <h4 :style="color">{{products[0]}}</h4>
      <p>{{price[0]}} 만원</p>
    </div>
    <div>
      <h4 :style="color">{{products[1]}}</h4>
      <p>{{price[1]}} 만원</p>
    </div>
    <div>
      <h4 :style="color">{{products[2]}}</h4>
      <p>{{price[2]}} 만원</p>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
        logo : '원룸샵',
        color : 'color : red;',
        products : ['역삼동원룸','청호동원룸','마포구원룸'],
        price : [60,70,80],
    }
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
  margin-top: 60px;
}
</style>
