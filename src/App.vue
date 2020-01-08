<template>
  <div id="app">
    <NavBar :missions="missions" />
    <AreaList :areas="areas" :missions="missions" class="mt-5" />
  </div>
</template>

<script>
import fs from "fs";

import NavBar from "./components/NavBar";
import AreaList from "./components/AreaList";

import area from "./assets/area.json";
import defaultMissions from "./assets/defaultMissions.json";

const rootDir = "./";

export default {
  name: "App",
  components: {
    NavBar,
    AreaList
  },
  data() {
    return {
      areas: area.data,
      missions: []
    };
  },
  methods: {
    readMissions: function() {
      console.log(defaultMissions);
      try {
        const data = fs.readFileSync(rootDir + "missions.json", "utf8");
        return JSON.parse(data).missions;
      } catch {
        return defaultMissions;
      }
    },
    saveMissions: function() {
      const data = JSON.stringify({ missions: this.missions });
      fs.writeFileSync(rootDir + "missions.json", data);
    }
  },
  created() {
    this.missions = this.readMissions();
    this.saveMissions();
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
