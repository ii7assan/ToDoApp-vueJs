<template>
  <!-- all the to do app components will be here and showed in ./view/Home page  -->
  <div>
    <v-container fluid>
      <v-row justify="center" align="center">
        <v-col>
          <v-card class="mx-auto" max-width="350">
            <v-card-title
              class="d-flex justify-space-between align-center text-capitalize"
            >
              <h3>to do list</h3>
              <h5>{{ toDosLenght }} Tasks</h5>
              <h5>{{ completedTasks }} Finished</h5>
            </v-card-title>
            <v-card-text>
              <InputTodo :toDos="toDos" />
              <ToDoList :toDos="toDos" />
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import ToDoList from "../components/listTodo.vue";
import InputTodo from './inputTodo.vue';
export default {
  components: {
    ToDoList,
    InputTodo,
  },
  data: () => ({
    toDos: [],
  }),
  computed: {
    toDosLenght() {
      return this.toDos.length || 0;
    },
    completedTasks() {
      return this.toDos.filter((task) => task.isDone).length;
    },
  },
};
</script>

<style>
.completed {
  text-decoration: line-through;
}
.delete:hover {
  color: red;
}
</style>