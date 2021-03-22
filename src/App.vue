<template>
  <v-app color="deep-purple">
    <v-app-bar max-height="70" class="grey darken-4 mb-4" dark>
      <v-row align="center" justify="center">
        <div class="d-flex align-center">
          <span>
            <h1 class="display font-weight-bold">Vue To Do</h1></span>
        </div>
      </v-row>
    </v-app-bar>
      <TodoList />
  </v-app>
</template>
<script>
import TodoList from "./components/TodoList.vue";

export default {
  name: "App",
  components: {
    TodoList,
  },
  data() {
    return {
      todos: [],
    };
  },

};

</script>

<style scoped>
.addButton {
  position: relative;
  margin: auto;
  margin-top: 20px;
  margin-bottom: 20px;
}
</style>