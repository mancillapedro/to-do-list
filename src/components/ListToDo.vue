<template>
  <ul>
    <li v-for="(tarea, i) in list" :key="i">
      {{ tarea }}
      <button @click="eliminar(i)">eliminar</button>
    </li>
  </ul>
</template>

<script>
export default {
  name: "ListToDo",
  props: {
    list: {
      type: Array,
      required: true,
    },
  },
  methods: {
    eliminar(i) {
      this.$emit("eliminar", { index: i });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  display: inline-block;
  margin: 0.5rem auto;
}
li {
  text-align: left;
  padding-top: 0.5rem;
}
</style>
