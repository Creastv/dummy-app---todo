<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>
<script>
export default {
  props: ["title"]
};
</script>
<style>
h1 {
  font-size: 51px;
  text-align: center;
}
</style>
