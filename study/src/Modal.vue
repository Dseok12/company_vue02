<template>
  <div
    class="black-bg"
    v-if="상태.모달창열렸니"
  >
    <div
      class="white-bg"
      @click.stop
    >
      <h4>{{ 상태.원룸들[상태.모달에보여줄물건순서].title }}</h4>
      <img
        :src="상태.원룸들[상태.모달에보여줄물건순서].image"
        :alt="상태.원룸들[상태.모달에보여줄물건순서].title"
        class="modal--image"
      />
      <p>{{ 상태.원룸들[상태.모달에보여줄물건순서].price }} 원</p>
      <p>{{ 상태.원룸들[상태.모달에보여줄물건순서].content }}</p>
      <!-- <button @click="상태.모달창열렸니 = false">닫기</button> -->
    </div>
  </div>
</template>
<script>
export default {
  name: 'Modal',
  props: {
    원룸들: {
      type: Array,
    },
    모달에보여줄물건순서: {
      type: Number,
    },
    모달창열렸니: {
      type: Boolean,
    },
  },
}
</script>
<style>
  
</style>