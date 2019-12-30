<template>
  <div>
    <Area
      v-for="id in Array.from(Array(areas.length).keys())"
      :key="id"
      :area="areas[id]"
      :missions="missions"
    />
  </div>
</template>

<script>
import Area from "@/components/Area";

export default {
  name: "AreaList",
  props: ["areas", "missions"],
  components: {
    Area
  },
  created() {
    console.log(this.contents);
  }
};
</script>

<style></style>
