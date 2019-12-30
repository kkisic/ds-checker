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
        :class="missions[id].status"
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
            <span class="dropdown-item"> Not Started </span>
            <span class="dropdown-item"> In Progress </span>
            <span class="dropdown-item"> Done </span>
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
