<template>
  <footer>
    <p>{{ inf }}</p>
  </footer>
</template>
<script>
export default {
  props: ["inf"]
};
</script>
<style>
footer {
  padding: 10px;
  background-color: aquamarine;
  position: fixed;
  bottom: 0px;
  width: 100%;
}
footer p {
  font-size: 12px;
  text-align: center;
}
</style>
