<template>
<!--
    - fetch() AJAX 통신 역할
    - Promise 객체는 비동기 작업이 맞이할 미래의 완료 또는 실패와 그 결과 값을 나타낸다
-->
  <div class="container">
    <p><button @click="getList">목록</button></p>
    <ul class="list-group">
        <li v-if="memoList.length == 0" class="list-group-item">게시물이 없습니다</li>
        <li v-for="memo in memoList" v-bind:key="memo.memono" class="list-group-item">{{ memo.subject }}<span class="badge">{{ memo.readcnt }}</span></li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      memoList: [] // 배열 변수 선언
    }
  },
  methods: {
    getList() {
      // alert()
      // fetch(요청명령어).then(응답메세지).then(출력)
      fetch('http://localhost:9000/memolist')
        .then((response) => { // 응답받았을때 어떻게 처리할지를 화살표 함수 {} 안에다 쓰면 된다
        // 메소드 체인형태라서 엔터치고 써도 연결되어 있다는 걸 안다
          if (response.ok) {
            // alert(response)         [object Response]
            // alert(response.json())  [object Promise] // 응답받은 값을 json 형태로 변환
            return response.json()
          }
        })
        .then((json) => {
          // alert(json)
          this.memoList = json
        })
    }
  }
}
</script>

<style>
  @import 'https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css';
</style>
