<template>
  <div class="home">
    <div class="main-title">
      KORONA TÜRKİYE
    </div>
    <div class="parent">
      <div class="div1 box">
        <p class="title">Toplam Vaka</p>
        <p class="number">{{ cases }}</p>
      </div>
      <div class="div2 box">
        <p class="title">Toplam Ölüm</p>
        <p class="number">{{ deaths }}</p>
      </div>
      <div class="div3 box">
        <p class="title">Tedavi Edilen</p>
        <p class="number">{{ recovered }}</p>
      </div>
      <div class="div7 box">
        <p class="title">Bugün Vaka</p>
        <p class="number">{{ todayCases }}</p>
      </div>
      <div class="div4 box">
        <p class="title">Aktif Vaka</p>
        <p class="number">{{ active }}</p>
      </div>
      <div class="div5 box">
        <p class="title">Kritik</p>
        <p class="number">{{ critical }}</p>
      </div>
      <div class="div6 box">
        <p class="title">Milyon Başına Ölüm</p>
        <p class="number">{{ deathsPerMillion }}</p>
      </div>
      <div class="div8 box">
        <p class="title">Milyon Başına Vaka</p>
        <p class="number">{{ casesPerOneMillion }}</p>
      </div>
      <div class="div9 box">
        <p class="title">Bugün Ölüm</p>
        <p class="number">{{ todayDeaths }}</p>
      </div>
      <div class="div10 box">
        <p class="title">Toplam Test</p>
        <p class="number">{{ tests }}</p>
      </div>
    </div>
    <p>rümeysa</p>
  </div>
</template>

<script>
const API_URL = "https://corona.lmao.ninja/v2/countries/turkey";
export default {
  data() {
    return {
      cases: "",
      deaths: "",
      recovered: "",
      active: "",
      critical: "",
      deathsPerMillion: '',
      todayCases: '',
      casesPerOneMillion: '',
      todayDeaths: '',
      tests: ''
    };
  },
  created() {
    fetch(API_URL)
      .then(response => {
        return response.json();
      })
      .then(data => {
        this.cases = data.cases;
        this.deaths = data.deaths;
        this.recovered = data.recovered;
        this.active = data.active;
        this.critical = data.critical;
        this.deathsPerMillion = data.deathsPerOneMillion
        this.todayCases = data.todayCases
        this.casesPerOneMillion = data.casesPerOneMillion
        this.todayDeaths = data.todayDeaths
        this.tests = data.tests
      });
  }
};
</script>

<style>
.home {
  padding-top: 40px;
  padding-left:20px;
  padding-right: 20px;
}

.main-title {
   font-size: 40px;
  font-weight: bold;
  color: #2c3e50;
}

.parent {
  display: grid;
  grid-gap: 10px;
  max-width: 1200px;
  margin: 0 auto;
  margin-top: 5rem;
  padding-bottom: 2rem;
}


@media (min-width: 600px) {
  .parent { grid-template-columns: repeat(2, 1fr); }
}

@media (min-width: 900px) {
  .parent {   grid-template-columns: repeat(3, 1fr); }
}
.title {
  font-size: 20px;
}

.number {
  font-size: 34px;
}

.box {
  border-radius: 4px;
  height: 200px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.parent div {
  color: #fff;
}

.div1 {
  
  background-color: #34495e;
}
.div2 {
  background-color: #c0392b;
}
.div3 {
  background-color: #27ae60;
}
.div4 {
  background-color: #2980b9;
}
.div5 {
  background-color: #e67e22;
}
.div6 {
  background-color: #e74c3c;
}
.div7 {
  background-color: #8e44ad;
}
.div8 {
  background-color: #16a085;
}
.div9 {
  background-color: #130f40;
}
.div10 {
  background-color: #130f40;
}
</style>
