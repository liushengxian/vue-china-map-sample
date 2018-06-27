<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li>
        <a href="https://vuejs.org" target="_blank">Vue Core Docs</a>
      </li>
      <li>
        <a href="https://github.com/liushengxian">My Github</a>
      </li>
      <li>
        <a href="https://misanya.com" target="_blank">Hello Misanya</a>
      </li>
    </ul>
    <h2>Open the console and check the output with your click on province. </h2>
    <china-map @click="handleClick" ref="chinamap"></china-map>
  </div>
</template>

<script>
import ChinaMap from "vue-china-map";

console.log("chinaMap is ", ChinaMap);
export default {
  name: "app",
  components: {
    ChinaMap
  },
  data() {
    return {
      msg: "Welcome to Vue-China-Map Plugin",
      subFeatureIndex: 0
    };
  },
  methods: {
    handleClick(properties, citylist) {
      console.log("click sample: ", properties, citylist);
      citylist.forEach(val => {
        val.selected = Math.random() > 0.5;
      });
      this.$refs.chinamap.setData(citylist, properties.subFeatureIndex);
    },
    testClick() {
      console.log("hello sample");
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
