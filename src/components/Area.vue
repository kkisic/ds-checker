<template>
  <div>
    <span>
      {{ area.name }}
    </span>
    <div v-for="key in range(area.startMissionId, area.endMissionId)" :key="key">

    </div>
  </div>
</template>

<script>
export default {
  name: 'Area',
  props: ['area']
}
</script>

<style>

</style>
