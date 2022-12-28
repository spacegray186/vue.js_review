<template>
  <img src="./assets/PC_05.jpg" style="width: 10%;">
  <hr>
  <!-- 1) 데이터 바인딩 (동적 바인딩, 양방향) -->
  <div>
    <h4 style="color: blue">OO원룸</h4>
    <p>{{ price1 }}만원</p>
  </div>
  <div>
    <h4 :style="style1">OO원룸</h4>
    <p>{{ price2 }}만원</p>
  </div>
  <hr>
  <!-- 2) 데이터 바인딩 (배열) -->
  <div>
    <h4>{{ products[0] }}</h4>
    <p>10 만원</p>
  </div>
  <div>
    <h4>{{ products[1] }}</h4>
    <p>30 만원</p>
  </div>
  <div>
    <h4>{{ products[2] }}</h4>
    <p>50 만원</p>
  </div>
  <hr>
  <!-- 3) 반복문 -->
  <div class="menu">
    <a>Home</a>
    <a>Products</a>
    <a>About</a>
  </div>
  <hr>
  <div class="menu">
    <a v-for="m in 3" :key="m">ITWILL</a>
  </div>
  <hr>
  <div class="menu">
    <a v-for="(m,i) in 3" :key="i">{{ i }}</a>
  </div>
  <hr>
  <div class="menu">
    <a v-for="m in menus" :key="m">{{ m }}</a>
  </div>
  <hr>
  <!-- 4) products를 반복문으로 해보자 -->
  <div v-for="(p, i) in products" :key="i">
    <h4>{{ p }}</h4>
    <p>10만원</p>
  </div>
  <hr>
  <!-- 5) 이벤트 핸들러 -->
  <div>
    <h4>{{ products[0] }}</h4>
    <p>10 만원</p>
    <!-- <button v-on:click="함수명">허위매물신고</button> -->
    <button @click="lieCount++">허위매물신고</button>
    <span> 신고수 : {{ lieCount }}</span>
  </div>
  <div>
    <h4>{{ products[1] }}</h4>
    <p>20 만원</p>
    <button @mouseover="lieCount++">허위매물신고</button>
    <span>신고수 : {{ lieCount }}</span>
  </div>
  <hr>
  <!-- 6) 이벤트와 함수 -->
  <div>
    <h4>{{ products[2] }}</h4>
    <p>30 만원</p>
    <button @click="increase">허위매물신고</button>
    <span>신고수 : {{ lieCount }}</span>
  </div>
  <hr>
  <!-- 7) 허위매물신고 각각 동작하기 -->
  <div>
    <h4>{{ products[0] }}</h4>
    <p>30 만원</p>
    <button @click="lieCounts[0] += 100">허위매물신고</button>
    <span>신고수 : {{ lieCounts[0] }}</span>
  </div>
  <div>
    <h4>{{ products[1] }}</h4>
    <p>20 만원</p>
    <button @click="lieCounts[1]++">허위매물신고</button>
    <span>신고수 : {{ lieCounts[1] }}</span>
  </div>
  <div>
    <h4>{{ products[2] }}</h4>
    <p>30 만원</p>
    <button @click="lieCounts[2]++">허위매물신고</button>
    <span>신고수 : {{ lieCounts[2] }}</span>
  </div>
</template>

<script>
//자바스크립트
//document.getElementById('아이디명').innerHTML=??
//제이쿼리
//$("#아이디명").html(??)
export default {
  name: 'App',
  components: {
  },
  data(){
    return {
      price1 : 60,
      price2 : 70,
      style1 : 'color:red',
      products : ['역삼동 원룸', '천호동 원룸', '서초동 원룸'],
      menus : ['HOME', 'SHOP', 'ABOUT'],
      lieCount : 0,
      lieCounts : [0, 0, 0]
    }
  },
  methods: {
    increase(){
      this.lieCount+=1;
    }
  },
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

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}
</style>
