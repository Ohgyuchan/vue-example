

<template>
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>
  <div>
    <p>{{ isPlatform() }}</p>
  </div>

  <div v-for="(product, index) in products" :key="index">
    <h3>{{ product }}</h3>
    <p>{{ prices[index] }}만원</p>
    <button class="button" @click="increaseReport(index)">허위매물신고</button>
    <span>신고수 : {{ reports[index] }}</span>
  </div>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      reports: [0, 0, 0],
      menus: ["Home", "Shop", "About", "Contact"],
      prices: [100, 200, 300],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
  },
  methods: {
    increaseReport(i) {
      this.reports[i] += 1;
    },
    overEffect() {
      // button hover event
    },
    isPlatform() {
      const info = navigator.userAgent;
      if (
        info.indexOf("iPhone") > -1 ||
        info.indexOf("iPad") > -1 ||
        info.indexOf("iPod") > -1
      ) {
        return "ios";
      } else if (info.indexOf("Android") > -1) {
        return "android";
      } else {
        return "PC";
      }
    },
  },
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.button {
  padding: 10px;
  background: darkslateblue;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.button:hover {
  background: darkblue;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>
