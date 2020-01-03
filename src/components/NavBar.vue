<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light fixed-top">
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <input
        class="form-control mr-sm-2"
        v-model="input"
        type="search"
        placeholder="101, 102, ..., etc"
        aria-label="Search"
      />
      <button
        class="btn btn-success mr-sm-2"
        v-on:click="changeStatuses(input, 'Done')"
      >
        Done
      </button>
      <button
        class="btn btn-danger mr-sm-2"
        v-on:click="changeStatuses(input, 'In Progress')"
      >
        In Progress
      </button>
      <button
        class="btn btn-secondary"
        v-on:click="changeStatuses(input, 'Not Started')"
      >
        Not Started
      </button>
    </div>
  </nav>
</template>

<script>
import fs from "fs";
import output from "@/assets/missions.json";

export default {
  name: "Navbar",
  props: ["missions"],
  methods: {
    parseId: function(input) {
      const regex = /[^0-9,]/g;
      return input
        .replace(regex, "")
        .split(",")
        .filter(x => {
          const n = parseInt(x);
          return n >= 100 && n <= 599;
        });
    },
    changeStatuses: function(input, status) {
      const ids = this.parseId(input);
      ids.forEach(id => (this.missions[id].status = status));
      this.updateJson();
    },
    updateJson: function() {
      fs.writeFileSync(output, JSON.stringify(this.missions));
    }
  }
};
</script>
