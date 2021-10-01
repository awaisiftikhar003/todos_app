<template>
  <header>
    <h1>{{ title }}</h1>
    <Button
      :text="!flag ? 'Add Task' : 'Close'"
      :color="!flag ? 'green' : 'red'"
      flag="flag"
      @add-task="$emit('add-task')"
    />
  </header>
</template>

<script>
import Button from "./Button.vue";
export default {
  name: "Header",
  //props object
  props: {
    title: String,
    flag: Boolean,
  },

  /* 
  you can define props as array 
  props:["tilte"]
  you can also define props as object too
  props:{
      title:{
          type:String,
          default:"Hello World"
      }
  }
  */
  //register child components
  components: {
    Button,
  },
  emits: ["add-task"],
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>