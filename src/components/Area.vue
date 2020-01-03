<template>
  <div>
    <span class="lead">
      {{ area.name }}
    </span>
    <div class="row row-cols-5">
      <div
        class="col"
        v-for="id of this.range"
        :key="id"
        :class="classByStatus(id)"
      >
        <p>No.{{ id }}</p>
        <div class="dropdown">
          <button
            class="btn btn-primary dropdown-toggle"
            type="button"
            id="dropdownStatusButton"
            data-toggle="dropdown"
            aria-haspopup="true"
            aria-expanded="false"
          >
            {{ missions[id].status }}
          </button>
          <div class="dropdown-menu" aria-labelledby="dropdownStatusButton">
            <span
              class="dropdown-item"
              v-on:click="missions[id].status = 'Not Started'"
            >
              Not Started
            </span>
            <span
              class="dropdown-item"
              v-on:click="missions[id].status = 'In Progress'"
            >
              In Progress
            </span>
            <span
              class="dropdown-item"
              v-on:click="missions[id].status = 'Done'"
            >
              Done
            </span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/js/bootstrap";
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";

export default {
  name: "Area",
  props: ["area", "missions"],
  methods: {
    classByStatus: function(id) {
      switch (this.missions[id].status) {
        case "Not Started":
          return "notStarted";
        case "In Progress":
          return "inProgress";
        case "Done":
          return "done";
        default:
          return "notStarted";
      }
    }
  },
  data() {
    return {
      length: this.area.endMissionId - this.area.startMissionId + 1,
      range: []
    };
  },
  created() {
    this.range = Array.from(
      Array(this.length).keys(),
      x => x + this.area.startMissionId
    );
    console.log(this.missions);
  }
};
</script>

<style>
.done {
  background: limegreen;
}

.notStarted {
  background: lightgray;
}

.inProgress {
  background: red;
}
</style>
