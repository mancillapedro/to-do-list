<template>
  <form id="FormComponent" @submit.prevent="newToDo">
    <legend>
      <h1 v-text="`Crea una nueva tarea`" />
    </legend>
    <label for="tarea" v-text="`Tarea`" />
    <input
      id="tarea"
      type="text"
      placeholder="Ingresa nueva tarea"
      v-model="inputTarea"
      autofocus
    />
    <button type="submit" v-text="`Añade`" :disabled="!inputTarea" />
  </form>
</template>

<script>
export default {
  name: "FormComponent",
  data: () => ({ inputTarea: null }),
  methods: {
    newToDo() {
      if (!this.inputTarea.trim()) return;
      this.$emit("newToDo", { tarea: this.inputTarea });
      this.inputTarea = null;
      this.$el[0].focus();
    },
  },
};
</script>