<template>
  <v-main class="addButton">
    <v-btn
      :disabled="dialog"
      :loading="dialog"
      fab
      color="deep-purple darken-2"
      @click="dialog = !dialog"
    >
      <v-icon>mdi-plus</v-icon>
    </v-btn>
    <v-dialog v-model="dialog" max-width="500px">
      <v-card>
        <v-card-text>
          <v-card-title>
            <h2 class="font-weight-bold" color="deep-purple darken-2">
              Add a To Do
            </h2>
          </v-card-title>
          <v-text-field v-model="title" label="Title" outlined> </v-text-field>
          <v-text-field v-model="content" label="Content" outlined>
          </v-text-field>
        </v-card-text>
        <v-card-actions>
          <v-btn
            justify="space-around"
            color="deep-purple darken-2"
            @click="addTodo(), (dialog = false)"
            >Add
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-main>
</template>

<script>
export default {
  name: "AddButton",

  data() {
    return {
      id: "1",
      title: "",
      content: "",
      done: false,
      dialog: false,
    };
  },
  methods: {
    addTodo() {
      const id = Math.floor(Math.random() * 100000);
      const title = this.title;
      const content = this.content;
      const done = true;
      if(!title){
        alert('Please add an title')
        return
       }
      this.$emit("create-todo", {
        id,
        title,
        content,
        done,
      });
     
      this.title='';
      this.content='';
    },
  },
};
</script>

<style>
</style>