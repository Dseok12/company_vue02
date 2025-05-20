<template>
  <!-- ========= -->
  <Modal
    :원룸들="상태.원룸들"
    :모달에보여줄물건순서="상태.모달에보여줄물건순서"
    v-if="상태.모달창열렸니"
  />

  <!-- ========= -->
  <nav class="menu">
    <div
      v-for="(메뉴, 순서) in 상태.메뉴들"
      :key="순서"
    >
      <a
        :href="메뉴.링크"
        class="menu--link"
        >{{ 메뉴.이름 }}</a
      >
    </div>
  </nav>


  <Discount />

  <!-- ========= -->
  <div
    v-for="(원룸, 순서) in 상태.원룸들"
    :key="원룸.id"
    class="item--container"
    @click="모달열기(순서)"
  >
    <img
      :src="원룸.image"
      :alt="원룸.title"
      class="item--image"
    />
    <div class="item--info">
      <h4>{{ 원룸.title }}</h4>
      <p>{{ 원룸.price }} 원</p>
    </div>
  </div>
  <!-- ========= -->
</template>

<script setup>
import { reactive } from 'vue';
import 원룸데이터 from './assets/oneroom.js'; // data가 아니라 default export라서 이름 아무거나 가능
import Discount from './Discount.vue'; // 할인 컴포넌트 import
import Modal from './Modal.vue'; // 모달 컴포넌트 import

// 반응형 데이터 선언
const 상태 = reactive({
  원룸들: 원룸데이터,
  모달창열렸니: false,
  모달에보여줄물건순서: 0,
  메뉴들: [
    { 이름: '홈', 링크: '/' },
    { 이름: '상담신청', 링크: '/counsel' },
    { 이름: '매물등록', 링크: '/register' },
  ],
  component: {
    Discount,
    Modal,
  }
});

// 모달 열기 함수
const 모달열기 = (순서) => {
  상태.모달창열렸니 = true;
  상태.모달에보여줄물건순서 = 순서;
};
</script>

<style>
/* 스타일 그대로 유지 */
.menu {
  display: flex;
  justify-content: center;
  background: linear-gradient(90deg, #4a00e0, #8e2de2);
  padding: 20px;
}

.menu .menu--link {
  color: white;
  font-weight: bold;
  padding: 12px 20px;
  margin: 0 8px;
  text-decoration: none;
  border-radius: 20px;
  transition: background 0.3s;
}

.menu .menu--link:hover {
  background: rgba(255, 255, 255, 0.2);
}

.item--container {
  width: 320px;
  background: #ffffff;
  margin: 20px auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  border-radius: 16px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  padding: 20px;
  transition: transform 0.3s, box-shadow 0.3s;
  cursor: pointer;
}

.item--container:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.15);
  background: #f9f9f9;
}

.item--info {
  margin-top: 12px;
  text-align: center;
}

.item--info h4 {
  font-size: 1.3rem;
  margin-bottom: 8px;
  color: #333;
}

.item--info p {
  font-size: 1rem;
  color: #777;
}

.item--image {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-radius: 12px;
}
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.6);
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  animation: fadeIn 0.3s ease-in-out;
}

.white-bg {
  width: 90%;
  max-width: 400px;
  background: #ffffff;
  border-radius: 16px;
  padding: 30px 20px;
  text-align: center;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
  animation: slideUp 0.4s ease;
}

.white-bg h4 {
  margin-bottom: 10px;
  font-size: 1.5rem;
  color: #333;
}

.white-bg p {
  margin-bottom: 20px;
  font-size: 1rem;
  color: #555;
}

.white-bg button {
  background: #00ba91;
  color: white;
  border: none;
  padding: 12px 24px;
  border-radius: 30px;
  font-size: 1rem;
  cursor: pointer;
  transition: background 0.3s ease;
}

.white-bg button:hover {
  background: #009c7c;
}
.modal--image {
  width: 100%;
  max-height: 250px;
  object-fit: cover;
  border-radius: 12px;
  margin-bottom: 20px;
}

/* 애니메이션 효과 추가 */
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes slideUp {
  from {
    transform: translateY(50px);
    opacity: 0;
  }
  to {
    transform: translateY(0);
    opacity: 1;
  }
}
</style>
