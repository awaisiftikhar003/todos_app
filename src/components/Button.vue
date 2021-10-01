<template>
  <button
    @click="$emit('add-task')"
    class="btn"
    :style="{ background: color }"
    id=""
  >
    {{ text }}
  </button>
</template>


<script>
export default {
  name: "Button",
  props: {
    text: String,
    color: String,
  },
};
</script>