<template>
  <div class="row">
    <div class="left-section">
      <div class="hyperhire-logo">
        <img src="logo.png" alt="Hyperhire Logo" width="60%" />
      </div>

      <div class="hyperhire-slogan">
        우리는 국가의 장벽을 넘어 최고의 인재를 매칭해드립니다.
      </div>

      <div class="hyperhire-contact">
        <p class="phone-number">010-0000-0000</p>
        <p class="email">aaaaa@naver.com</p>
      </div>
    </div>
    <div class="right-section">
      <div class="card-container">
        <q-card class="card" v-for="(card, index) in cards" :key="index">
          <q-card-section class="icon-section">
            <div class="icon-box">
              <q-icon :name="card.icon" size="2em" color="grey-7" />
            </div>
          </q-card-section>
          <q-card-section>
            <div class="card-title">{{ card.title }}</div>
            <div class="card-content">
              바로가기
            </div>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </div>
  <div class="row text-row">
    <div class="column" v-for="(item, index) in companyData" :key="index">
      <p class="top-text">{{ item.category }}</p>
      <p class="middle-text">{{ item.value }}</p>
      <p v-if="item.additionalValue" class="bottom-text">{{ item.additionalValue }}</p>
    </div>
  </div>
</template>

<script>

import { ref } from 'vue';

export default {


setup(){
const cards = ref([
  {
    icon: 'code',
    title: '해외 개발자 원격 채용',
  },
  {
    icon: 'person',
    title: '외국인 원격 채용 (비개발)',
  },
  {
    icon: 'translate',
    title: '한국어 가능 외국인 채용',
  },
  {
    icon: 'settings',
    title: '해외 개발자 활용 서비스',
  }
]);

const companyData = [
  { category: "상호명", value: "하이퍼하이어", additionalValue: "Hyperhire India Private Limited"},
  { category: "대표 CEO", value: "김주현", additionalValue: "Juhyun Kim"},
  { category: "사업자등록번호 CIN", value: "427-86-01187", additionalValue:"U74110DL2016PTC290812"},
  { category: "주소 ADDRESS", value: "서울특별시 강남대로 479, 지하1층 238호", additionalValue: "D-138, Street number 11, Jagjeet Nagar, North East Deli 110053 India"}
];
return {cards, companyData}
}
}
</script>

<style scoped lang="scss">
.row {
  display: flex;
  flex-wrap: wrap;
}

.left-section {
  display: flex;
  flex-direction: column;
  align-items: left;
  justify-content: left;
  padding: 30px;
  text-align: left;
  flex: 1;
}

.hyperhire-logo {
  margin-bottom: 20px;
}

.hyperhire-slogan {
  font-size: 14px;
  margin-bottom: 20px;
}

.hyperhire-contact {
  p {
    margin: 5px 0;
    font-size: 1.1em;
    color: #5e626e;
    font-weight: 900;
  }

}

.right-section {
  flex: 2;
  /* Takes 2/3 of the row by default */
}

.card-container {
  display: flex;
  justify-content: space-between;
  /* Distribute cards evenly */
  flex-wrap: wrap;
}

.card {
  width: 100%;
  max-width: 23%;
  /* Adjust for 4 cards in a row with some margin */
  margin: 1%;
  border: none;
  /* Remove default border */
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  padding: 5px;
}

.icon-section {
  text-align: left;
  /* Center the icon */
  padding: 10px;
}

.card-title {
  font-size: 1.2em;
  font-weight: 900;
  text-align: left;
  padding-bottom: 6px;
}

.card-content {
  text-align: left;
  font-size: 1.2em;
  padding-bottom: 5px;
  padding-top: 5px;
}

.icon-box {
  background-color: #f5f5f5;
  /* Light gray background */
  padding: 15px;
  border-radius: 8px;
  /* Rounded corners */
  display: inline-flex;
  /* Center the icon */
}

/* Responsive adjustments for smaller screens */
@media (max-width: 1024px) {
  .card {
    max-width: 48%;
    /* Two cards per row */
  }
}

@media (max-width: 600px) {
  .left-section {
    flex: 1 100%;
    /* Take full width on small screens */
  }

  .right-section {
    flex: 1 100%;
    /* Take full width on small screens */
  }

  .card {
    max-width: 100%;
    /* One card per row */
  }
}

.text-row {
  display: grid;
  /* Use grid for better control */
  grid-template-columns: repeat(4, 1fr);
  /* 4 equal columns */
  gap: 10px;
  /* Adjust spacing between columns */
  padding: 30px;
  margin-top: 50px;
}

.column {
  text-align: left;
  /* Align text to the left */
}

.top-text {
  font-weight: 900;
}

.bottom-text {
  margin-top: 2px;
  font-weight: 900;
  color: #5e626e;
}

/* Responsive adjustments */
@media (max-width: 1024px) {
  .row {
    grid-template-columns: repeat(4, 1fr);
    /* 2 columns */
  }
}

@media (max-width: 600px) {
  .row {
    grid-template-columns: repeat(1, 1fr);
    /* 1 column */
  }
}
</style>
