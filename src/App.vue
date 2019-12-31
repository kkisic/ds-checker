<template>
  <div id="app">
    <NavBar />
    <AreaList :areas="areas" :missions="missions" />
  </div>
</template>

<script>
import NavBar from "./components/NavBar";
import AreaList from "./components/AreaList";

import area from "./assets/area.json";
import missions from "./assets/missions.json";

export default {
  name: "App",
  components: {
    NavBar,
    AreaList
  },
  data() {
    return {
      areas: area.data,
      missions: missions.missions
    };
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
  padding: 30px;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
