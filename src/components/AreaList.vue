<template>
  <div>
    <Area
      v-for="id in Array.from(Array(areas.length).keys())"
      :key="id"
      :area="areas[id]"
      :missions="missions"
      @save="emitParent"
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
  methods: {
    emitParent: function() {
      this.$emit("save");
    }
  }
};
</script>

<style></style>
