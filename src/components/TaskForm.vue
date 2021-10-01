<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="text" v-model="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Short Description</label>
      <input
        type="text"
        v-model="desc"
        name="desc"
        placeholder="Short Description"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Status</label>
      <input type="checkbox" v-model="status" name="status" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block btn-primary" />
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: "",
      desc: "",
      status: false,
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      if (!this.text) {
        alert("Please add a task");
        return;
      }
      const newTask = {
        id: Math.floor(Math.random() * 100000),
        text: this.text,
        desc: this.desc,
        status: this.status,
      };
      this.$emit("save-task", newTask);
      this.text = "";
      this.desc = "";
      this.status = false;
    },
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
  text-align: start;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>