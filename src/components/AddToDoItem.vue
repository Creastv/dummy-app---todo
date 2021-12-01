<template>
  <div class="wraper-form">
    <form class="add-form" @submit.prevent="submitData" v-if="disForm">
      <div class="warning" v-if="warning">
        <h3>{{ emptyFilds }}</h3>
      </div>
      <a href="#" class="close" @click="displayForm">Close x</a>
      <label for="title">Title:</label>
      <input
        type="text"
        id="title"
        name="title"
        placeholder="Title"
        v-model="title"
      />
      <label for="desc">Description:</label>
      <textarea
        type="text"
        id="desc"
        name="desc"
        placeholder="Description"
        v-model="desc"
      />
      <div class="wraper-btn">
        <button type="submit">Add Item</button>
      </div>
    </form>
    <div class="wraper-btn">
      <a href="#" class="btn btn-d-form" v-if="!disForm" @click="displayForm">{{
        !disForm ? "Add new iteam" : " Hide add form"
      }}</a>
    </div>
  </div>
</template>

<script>
export default {
  emits: ["add-item"],
  data() {
    return {
      title: "",
      desc: "",
      disForm: false,
      warning: false,
      emptyFilds: "Can't left empty fields!"
    };
  },

  methods: {
    submitData() {
      if (this.title == "" || this.desc == "") {
        this.warning = true;
      } else {
        this.$emit("add-item", this.title, this.desc);
        this.title = "";
        this.desc = "";
        this.warning = false;
      }
    },
    displayForm() {
      this.disForm = !this.disForm;
      //   document.body.scrollTop = document.body.scrollHeight;
    }
  }
};
</script>

<style scope>
.wraper-form {
  position: relative;
  width: 80%;
  margin: 0 auto;
  padding: 15px;
}
.add-form input,
.add-form textarea,
.add-form label {
  display: block;
}
.add-form input,
.add-form textarea {
  width: 100%;
  margin-bottom: 10px;
  padding: 10px;
  border-radius: 10px;
  box-shadow: none;
  border: 1px solid #e7e7e7;
}
.close {
  position: absolute;
  right: 10px;
  top: 10px;
  color: red;
  text-decoration: none;
}
.warning {
  padding: 2px 10px;
  margin: 20px 0;
  text-align: center;
  background-color: rgb(255, 213, 213);
  border-radius: 10px;
  width: 100%;
}
.wraper-btn {
  text-align: center;
  width: 100%;
}
.wraper-btn .btn {
  display: inline-block;
  text-align: center;
}
@media only screen and (max-device-width: 480px) {
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
