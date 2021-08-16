<template>
  <div>
    <v-list v-for="(toDo, i) in toDos" :key="i">
      <v-list-item>
        <template>
          <v-list-item-action>
            <v-checkbox v-model="toDo.isDone"></v-checkbox>
          </v-list-item-action>
          <!-- show to do -->
          <v-list-item-content>
            <v-list-item-subtitle :class="toDo.isDone ? 'completed' : ''">
                {{toDo.text}}
            </v-list-item-subtitle>
          </v-list-item-content>

          <!-- Delete todo -->
          <v-list-item-action>
            <v-btn icon @click="deleteToDo(i)">
              <v-icon color="grey lighten-1" class="fas fa-trash"></v-icon>
            </v-btn>
          </v-list-item-action>
        </template>
      </v-list-item>
      <v-divider></v-divider>
    </v-list>
  </div>
</template>

<script>
export default {
    props: {
        toDos: Array
    },
    methods: {
        deleteToDo(index){
                this.toDos.splice(index,1);
        }
    }
};
</script>

<style>
.completed{
    text-decoration:  line-through;
}
</style>