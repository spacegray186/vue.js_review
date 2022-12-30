<template>
  <!-- 1) 문자열 바인딩 - 단방향 -->
  <div><!-- 최상위 태그가 있어야 함.(필수) -->
    <h1>Hello {{ userName }}</h1>
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  // function data(){}  function 생략가능
  data() {
    return {
      userName: 'John Doe',
      message: '서울특별시'
    }
  }
}
</script>
