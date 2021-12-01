<template>
  <div>
    <Header :title="headerTitle" />
    <main>
      <hr />
      <Statistic
        :allIteams="toDoList.length"
        :itemsDone="statsDone"
        :itemsPri="statsPriority"
      />
      <Items
        :toDoList="toDoList"
        @mark-as-done="itemDone"
        @mark-as-important="itemImportant"
      />
      <hr />
      <AddToDoItem @add-item="addItem" />
    </main>
    <Footer :inf="footerInf" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import Items from "./components/Items.vue";
import Statistic from "./components/Statistic.vue";
import AddToDoItem from "./components/AddToDoItem.vue";

export default {
  name: "App",
  components: {
    Header,
    Footer,
    Items,
    Statistic,
    AddToDoItem
  },
  data() {
    return {
      headerTitle: "Welcome to ToDoApp!",
      footerInf: "Copyright creastv.pl",
      statsPriority: 0,
      statsDone: 0,
      toDoList: [
        {
          id: "1",
          title: "Start to programing",
          desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
          done: false,
          priority: false
        },
        {
          id: "2",
          title: "Learn Vue.js",
          desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
          done: false,
          priority: false
        }
      ]
    };
  },
  watch: {
    toDoList: {
      handler() {
        const itemDone = this.toDoList.filter((done) => done.done);
        const itemPriority = this.toDoList.filter(
          (priority) => priority.priority
        );
        this.statsDone = itemDone.length;
        this.statsPriority = itemPriority.length;
        console.log(itemDone.length, itemPriority.length);
      },
      deep: true
    }
  },
  methods: {
    itemDone(id) {
      const idItem = this.toDoList.find((toDo) => toDo.id === id);
      idItem.done = !idItem.done;
    },
    itemImportant(id) {
      const idItem = this.toDoList.find((toDo) => toDo.id === id);
      idItem.priority = !idItem.priority;
    },

    addItem(title, desc) {
      let id = String(this.toDoList.length + 1);
      const newIteam = {
        id: id,
        title: title,
        desc: desc,
        done: false,
        priority: false
      };
      this.toDoList.push(newIteam);
    }
  }
};
</script>

<style>
html,
body {
  margin: 0;
  padding: 0;
}
main {
  max-width: 900px;
  width: 90%;
  margin: 0px auto;
  /* padding: 0 15px; */
  padding-bottom: 100px;
}
</style>
