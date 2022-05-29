<template>
  <div id="app">
    <form @submit.prevent="addToDo">
      <legend><h1>Crea una nueva tarea</h1></legend>
      <label for="tarea">Tarea</label>
      <input
        id="tarea"
        type="text"
        placeholder="Ingresa nueva tarea"
        v-model="inputTarea"
      />
      <button type="submit">Añade</button>
    </form>
    <list-to-do :list="lista" @eliminar="eliminar" />
  </div>
</template>

<script>
import ListToDo from "./components/ListToDo.vue";

export default {
  name: "App",
  components: {
    ListToDo,
  },
  data() {
    return {
      inputTarea: "",
      lista: [],
    };
  },
  methods: {
    addToDo() {
      if (this.inputTarea.trim()) this.lista.push(this.inputTarea);
      this.inputTarea = "";
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
