<template>
  <ul>
    <li v-for="(tarea, i) in list" :key="i">
      {{ `${i + 1}: ${tarea}` }}
      <button @click="eliminar(i)" v-text="`eliminar`" />
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
