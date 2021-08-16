<template>
  <v-form ref="ToDoList" @submit.prevent="createToDo()" v-model="valid">
    <v-text-field
      name="toDo"
      label="what's your to do today?"
      v-model="toDoTitle"
      :rules="nameRules"
      solo
    ></v-text-field>
    <div v-if="toDos.length == 0">None To Dos Currently 😊</div>
  </v-form>
</template>

<script>
export default {
  data: () => ({
    valid: false,
    nameRules: [(v) => !!v || "TO Do is required"],
    toDoTitle: "",
  }),
  props: {
    toDos: Array,
  },
  methods: {
    createToDo() {
      if (this.valid) {
        this.toDos.push({ isDone: false, text: this.toDoTitle });
        this.toDoTitle = "";
        this.$refs.ToDoList.reset();
      }
    },
  },
};
</script>

<style>
</style>