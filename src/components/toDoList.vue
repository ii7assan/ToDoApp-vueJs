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
              <h5 class="text-right">{{ toDosLenght }} Tasks</h5>
            </v-card-title>
            <v-card-text>
              <v-form
                ref="ToDoList"
                @submit.prevent="createToDo()"
                v-model="valid"
              >
                <v-text-field
                  name="toDo"
                  label="what's your to doo today?"
                  v-model="toDoTitle"
                  :rules="nameRules"
                  solo
                ></v-text-field>
              </v-form>

              <v-list v-for="(toDo, i) in toDos" :key="i">
                <v-list-item>
                  <template v-slot:default="{ active }">
                    <v-list-item-action>
                      <v-checkbox :input-value="active"></v-checkbox>
                    </v-list-item-action>
                    <!-- show to do -->
                    <v-list-item-content>
                      <v-list-item-title></v-list-item-title>
                      <v-list-item-subtitle>{{
                        toDo.text
                      }}</v-list-item-subtitle>
                    </v-list-item-content>

                    <!-- Delete todo -->
                    <v-list-item-action>
                      <v-btn icon @click="deleteToDo(i)">
                        <v-icon color="grey lighten-1">mdi-information</v-icon>
                      </v-btn>
                    </v-list-item-action>
                  </template>
                </v-list-item>
                <v-divider></v-divider>
              </v-list>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  data: () => ({
    toDos: [],
    toDoTitle: "",
    nameRules: [
      (v) => !!v || "TO Do is required",
    ],
    valid: false,
  }),
  computed: {
    toDosLenght() {
      return this.toDos.length || 0;
    },
  },
  methods: {
    createToDo() {
      if (this.valid) {
        this.toDos.push({ isDone: false, text: this.toDoTitle });
        this.toDoTitle = "";
        this.$refs.ToDoList.reset();
      }
    },
    deleteToDo(index) {
      this.toDos.splice(index, 1);
    },
  },
};
</script>

<style>
</style>