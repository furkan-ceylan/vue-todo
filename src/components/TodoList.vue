<template>
  <div class="mx-auto d-flex align-center flex-column mb-12">
    <AddButton @create-todo="addTodo" class="mb-8" />
    
    <ul>
      <li>
        
        <v-card
          v-for="todo in todos"
          :key="todo.id"
          class="mx-auto d-flex flex-column mb-6"
          color="deep-purple"
          dark
          max-width="400"
          min-width="300"
        >
        <div v-if="todo.done">
          <v-toolbar flat color="deep-purple" dark>
            <v-toolbar-title>
              <span class="headline font-weight-bold">
                {{todo.title}}</span>
            </v-toolbar-title>
            <v-spacer></v-spacer>
            <v-btn icon @click="deleteTodo(todo.id)">
              <v-icon>mdi-close</v-icon>
            </v-btn>
          </v-toolbar>
          <v-list-item class="grow">
            <v-row>
              <v-card-text class="title font-weight-light">
                {{ todo.content }}
              </v-card-text>
            </v-row>
          </v-list-item>
        </div>
        </v-card>
      </li>
    </ul>
    
  </div>
</template>

<script>
import AddButton from "./AddButton.vue";
export default {
  name: "TodoList",
  props: ["todos"],
  components: {
    AddButton,
  },
  created() {
    this.todos = [
      {
        id: 1,
        title: "Todo A",
        content: "Project A",
        done: true,
      },
      {
        id: 2,
        title: "Todo B",
        content: "Project B",
        done: true,
      },
      {
        id: 3,
        title: "Todo C",
        content: "Project C",
        done: true,
      },
    ];
    
  },
    methods: {
    addTodo(addTodo) {
      this.todos.push(addTodo);
    },
    deleteTodo(id){
      if(confirm("Are you sure you finished this to do?"))
      this.todos = this.todos.filter((todos) => todos.id !== id)
    }
  },
};
</script>


<style scoped>
ul {
  list-style-type: none;
}
</style>
