<template>
  <div>
    <div :class="{ 'text-red': true }">클래스 바인딩1</div>
    <div :class="{ 'text-red': false }">클래스 바인딩2</div>
    <div :class="{ 'text-red': true, 'active': true }">클래스 바인딩3</div>
    <div :class="{ 'text-red': true, active: true }">클래스 바인딩4</div>
    <!-- 선택자명이 두개의 단어로 구성되어 있으면 ' 기호 생략시 에러
    <div :class="{ text-red: true }">클래스 바인딩1</div>
    -->
    <div :class="{ 'text-red': hasError, 'active': isActive }">클래스 바인딩5</div>
    <div @click="trueForm" :class="{ 'text-red': hasError, 'active': isActive }">클릭시 method로 클래스 바인딩</div>
    <!-- class를 배열로 저장후 적용. 실무에서 그렇게 많이 사용하지는 않음 -->
    <div :class="class2">클래스 바인딩6</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      hasError: false,
      isActive: false,
      class2: ['active', 'text-red']
    }
  },
  methods: {
    trueForm() {
      this.hasError = true
      this.isActive = true
    }
  }
}
</script>

<!-- 현재 문서에서만 스타일 적용 -->
<style scoped>
  .active { background-color: greenyellow; font-weight: bold; }
  .text-red { color: red; }
</style>
