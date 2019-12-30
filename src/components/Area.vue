<template>
  <div>
    <span>
      {{ area.name }}
    </span>
    <div class="row row-cols-5">
      <div class="col" v-for="id of this.range" :key="id">
        <div :class="missions[id].status">
          <p>No.{{ id }}</p>
          <p>
            {{ missions[id].status }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
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
