<template>
  <div>
    <h3>문자열 바인딩</h3>
    <input type="text" v-model="userId">
    <hr>

    <h3>이벤트</h3>
    <!-- 기본형 <button onclick="myFunction()"></button> -->
    <button @click="myFunction">클릭</button> <!-- 함수 뒤에 () 들어가면 에러 -->
    <!-- <button @click="myFunction">클릭</button> // 파라미터가 없다면 () 생략가능 -->
    <button @click="changeData">변경</button>
    <hr>

    <h3>숫자 바인딩</h3>
    <input type="text" v-model="num1">
    <input type="text" v-model="num2">
    <span>{{ num1 + num2 }}</span>
    <br>
    <input type="text" v-model.number="num3">
    <input type="text" v-model.number="num4">
    <span>{{ num3 + num4 }}</span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userId: 'itwill',
      num1: 0,
      num2: 0,
      num3: 0,
      num4: 0
    }
  },
  methods: {
    myFunction() { // function 생략
      alert(this.userId) // ; 입력시 오류
    },
    changeData() {
      this.userId = 'Korea'
    }
  }
}
</script>
