<template>
  <!-- =====메뉴====== -->
  <div class="menu">
    <a v-for="(작명, idx) in 메뉴들" :key="idx"> {{ 작명 }}</a>
  </div>
  <!-- =====메뉴====== -->

  <!-- ====모달창===== -->
  <div class="black-bg" v-if="모달창열렸니">
    <div class="white-bg" @click="모달창열렸니 = false">
      <h4>상세페이지</h4>
      <p>상세페이지내용임</p>
    </div>
  </div>
  <!-- ====모달창===== -->

  <!-- =======리스트======== -->
  <div v-for="(물건, idx) in 물건들" :key="idx" @click="모달창열렸니 = true">
    <img src="./assets/room0.jpg" class="room-img" alt="">
    <h4>{{물건들[idx]}}</h4>
    <p>50만원</p>
  </div>
  <!-- =======리스트======== -->
</template>

<script>
export default {
  name : 'App',
  data(){
    return {
      모달창열렸니 : false,
      물건들 : [ '역삼동원룸', '천호동원룸', '마포구원룸' ],
      메뉴들 : ['Home', 'Shop', 'About'],
    }
  }
}

</script>

<style>
.room-img{
  width: 100%;
  margin-top: 40px;
}
.menu {
  background : darkslateblue;
  padding : 15px;
  border-radius : 5px;
}
.menu a {
  color : white;
  padding : 10px;
}

.black-bg {
  width: 100%; height:100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
} 
</style>