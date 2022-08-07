<template>
  <div id="app">
    <form-component @newToDo="addToDo" />
    <list-to-do :list="lista" @eliminar="eliminar" />
  </div>
</template>

<script>
import FormComponent from "./components/FormComponent.vue";
import ListToDo from "./components/ListToDo.vue";

export default {
  name: "App",
  components: {
    ListToDo,
    FormComponent,
  },
  data: () => ({ lista: [] }),
  methods: {
    addToDo({ tarea }) {
      this.lista.push(tarea);
    },
    eliminar({ index }) {
      this.lista.splice(index, 1);
    },
  },
  beforeCreate() {
    document.title = "Trabajando con Props | To Do List";
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
  width: 100%;
}
form > * {
  margin: 0 0.25rem;
}
</style>
