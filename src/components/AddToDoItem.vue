<template>
  <div class="wraper-form">
    <Modal v-if="disForm">
      <template #close>
        <button class="close" @click="displayForm">Close x</button>
      </template>
      <template #header> Add to do item </template>
      <template #warning v-if="warning">
        <p>{{ emptyFilds }}</p>
      </template>
      <template #content>
        <form class="add-form" @submit.prevent="submitData">
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
            <button type="submit" class="btn">Add Item</button>
          </div>
        </form>
      </template>
    </Modal>
    <div class="wraper-btn">
      <a
        href="#"
        class="btn btn-d-form"
        v-if="!disForm"
        @click.prevent="displayForm"
        >{{ !disForm ? "Add new iteam" : " Hide add form" }}</a
      >
    </div>
  </div>
</template>

<script>
import Modal from "./Modal.vue";
export default {
  emits: ["add-item"],
  components: {
    Modal,
  },
  data() {
    return {
      title: "",
      desc: "",
      disForm: false,
      warning: false,
      emptyFilds: "Can't left empty fields!",
    };
  },

  methods: {
    submitData() {
      if (this.title == "" || this.desc == "") {
        this.warning = !this.warning;
      } else {
        this.$emit("add-item", this.title, this.desc);
        this.title = "";
        this.desc = "";
        this.warning = false;
        this.displayForm();
      }
    },
    displayForm() {
      this.disForm = !this.disForm;
    },
    closeWarning() {
      this.warning = false;
    },
  },
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
.wraper-btn {
  text-align: center;
  width: 100%;
}
.wraper-btn .btn {
  display: inline-block;
  text-align: center;
}
.warning p {
  background: orange;
  padding: 5px 10px;
  margin: 10px 0px;
  width: 100%;
  border-radius: 6px;
}
</style>
