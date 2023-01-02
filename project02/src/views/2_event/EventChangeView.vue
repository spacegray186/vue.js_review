<template>
  <div>
    <!-- 이벤트 v-on:change=""의 축약형 @change -->
    <select name="" id="" @change="changeCity" v-model="selectedCity">
        <option value="">== 도시선택 ==</option>
        <option :value="city.cityCode" v-for="city in cityList" :key="city.cityCode">{{ city.title }}</option>
    </select>
    <select name="" id="">
      <option :value="dong.dongCode" v-for="dong in selectedDongList" :key="dong.dongCode">{{ dong.dongTitle }}</option>
    </select>
    <hr>

    <!-- 양방향이기 때문에 change 이벤트를 사용하지 않고도 구현 가능 (단, 가독성이 떨어지므로 비추천) -->
    <select name="" id="" v-model="selectedCity">
      <option value="">== 도시선택 ==</option>
      <option :value="city.cityCode" v-for="city in cityList" :key="city.cityCode">{{ city.title }}</option>
    </select>
    <select name="" id="">
      <option :value="dong.dongCode" :key="dong.dongCode" v-for="dong in dongList.filter(dong=>dong.cityCode===selectedCity)">{{ dong.dongTitle }}</option>
    </select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedCity: '', // 02 | 051 | 064  저장
      cityList: [
        { cityCode: '02', title: '서울' },
        { cityCode: '051', title: '부산' },
        { cityCode: '064', title: '제주' }
      ],
      dongList: [
        { cityCode: '02', dongCode: '1', dongTitle: '서울 1동' },
        { cityCode: '02', dongCode: '2', dongTitle: '서울 2동' },
        { cityCode: '02', dongCode: '3', dongTitle: '서울 3동' },
        { cityCode: '02', dongCode: '4', dongTitle: '서울 4동' },
        { cityCode: '051', dongCode: '1', dongTitle: '부산 1동' },
        { cityCode: '051', dongCode: '2', dongTitle: '부산 2동' },
        { cityCode: '051', dongCode: '3', dongTitle: '부산 3동' },
        { cityCode: '064', dongCode: '1', dongTitle: '제주 1동' },
        { cityCode: '064', dongCode: '2', dongTitle: '제주 2동' }
      ],
      selectedDongList: [] // 해당하는 동만 걸러서 저장. 예) 서울1동 ~ 서울4동
      // 선택한 결과값를 저장
    }
  },
  methods: {
    changeCity() {
      // alert(this.selectedCity) 02 | 051 | 064

      // 선택한 cityCode가 02라면 dongList에서 02만 걸러내서 가져옴
      this.selectedDongList = this.dongList.filter(dong => dong.cityCode === this.selectedCity)

      // alert(this.selectedDongList)
      //예) { cityCode: '064', dongCode: '1', dongTitle: '제주 1동' }
      //    { cityCode: '064', dongCode: '2', dongTitle: '제주 2동' }
    }
  }
}
</script>
