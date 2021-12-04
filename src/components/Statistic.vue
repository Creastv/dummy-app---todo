<template>
  <div class="stat">
    <span>Statistics:</span>
    <span>Complete: {{ itemsDone }} / {{ allIteams }}</span>
    <span>High priority: {{ itemsPri }} / {{ allIteams }} </span>
  </div>
</template>

<script>
export default {
  props: ["allIteams", "itemsDone", "itemsPri"]
};
</script>
<style>
.stat {
  text-align: center;
}
.stat span {
  padding: 5px 10px;
}
</style>
