<template>
  <li class="cart" :class="statusCartClass()">
    <div class="left">
      <span>{{ id }}</span>
    </div>
    <div class="middle">
      <h2>{{ title }}</h2>
      <p>{{ desc }}</p>
    </div>
    <div class="right">
      <button :id="id" class="btn" @click="itemDone">
        {{ done ? "Complete" : "Mark as complete" }}
      </button>
      <button :id="id" class="btn" @click="itemImportant">
        {{ priority ? "High priority" : "Mark as high priority" }}
      </button>
    </div>
  </li>
</template>

<script>
export default {
  props: ["id", "title", "desc", "done", "priority"],
  methods: {
    itemDone() {
      this.$emit("mark-as-done");
    },
    itemImportant() {
      this.$emit("mark-as-important");
    },
    statusCartClass() {
      if (this.done && this.priority) {
        return "done priority";
      } else if (this.done) {
        return "done";
      } else if (this.priority) {
        return "priority";
      }
    },
  },
};
</script>

<style>
.cart {
  margin-bottom: 20px;
  padding: 5px;
  border-radius: 6px;
  box-shadow: 0px 4px 0px 5px #e7e7e7;
  display: flex;
}
.left {
  padding: 26px 10px 10px;
  align-self: flex-start;
}
.middle {
  padding: 0px 10px;
  width: 80%;
  flex: auto;
}
.right {
  width: 20%;
}
.btn {
  padding: 10px;
  border-radius: 6px;
  border: 1px solid #e7e7e7;
  box-shadow: 0px 2px 0px 0px #e7e7e7;
  margin: 10px;
  text-decoration: none;
  color: rgb(0, 174, 116);
  background-color: aquamarine;
  display: block;
  text-align: center;
}
.cart.done {
  box-shadow: 0px 4px 0px 5px rgb(101, 197, 138);
  color: green;
}
.cart.priority {
  box-shadow: 0px 4px 0px 5px rgb(255, 185, 185);
  color: red;
}
.cart.done.priority {
  box-shadow: 0px 4px 0px 5px rgb(224, 248, 6);
  color: rgb(167, 197, 32);
}
@media only screen and (max-device-width: 580px) {
  .cart {
    flex-wrap: wrap;
  }
  .middle {
    width: 100%;
  }
  .right {
    width: 100%;
  }
  .wraper-btn .btn-d-form {
    position: fixed;
    left: 0;
    bottom: 60px;
    width: 90%;
  }
}
</style>
