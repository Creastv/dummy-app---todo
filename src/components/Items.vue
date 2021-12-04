<template>
  <ul>
    <Item
      v-for="toDo in toDoList"
      :key="toDo.id"
      :id="toDo.id"
      :title="toDo.title"
      :desc="toDo.desc"
      :done="toDo.done"
      :priority="toDo.priority"
      @mark-as-done="itemDone"
      @mark-as-important="itemImportant"
    ></Item>
  </ul>
</template>

<script>
import Item from "./Item.vue";
export default {
  props: ["toDoList"],
  components: { Item },
  methods: {
    itemDone() {
      this.$emit("mark-as-done", event.target.id);
    },
    itemImportant() {
      this.$emit("mark-as-important", event.target.id);
    }
  }
};
</script>

<style>
ul {
  display: block;
  width: 100%;
  padding: 10px;
  list-style: none;
}
</style>
