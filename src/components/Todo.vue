<template>
    <div class="ui centered card">
       <!-- Todo shown when we are not in editing mode -->
      <div class="content" v-show="!isEditing">
        <div class="header">
          {{todo.title}}
        </div>
        <div class="meta">
          {{todo.project}}
        </div>
        <div class="extra content">
          <span class="right floated edit icon" v-on:click="showForm">
            <i class="edit icon"></i>
          </span>
          <!-- Delete Button Here -->
          <span class="right floated trash icon" v-on:click="deleteTodo(todo)">
            <i class="trash icon"></i>
          </span>
        </div>
      </div>
      <!-- Form is visible when we are in editing mode -->
      <div class="content" v-show="isEditing">
        <div class="ui form">
          <div class="field">
            <label for="">Title</label>
            <input type="text" v-model="todo.title" name="" value="">
          </div>
          <div class="field">
            <label for="">Project</label>
            <input type="text" v-model="todo.project" name="" value="">
          </div>
          <div class="ui tow button attached buttons">
            <button class="ui basic blue button" name="button" v-on:click="hideForm">Close X</button>

          </div>

        </div>
      </div>
      <div class="ui bottom attached green basic button" v-show="!isEditing && todo.done">
        Completed
      </div>
      <div class="ui bottom attached red basic button" v-show="!isEditing && !todo.done">
        Pending
      </div>
    </div>
</template>

<script>
export default {
  props: ['todo'],
  data() {
    return {
      isEditing: false,
    };
  },
  methods: {
    deleteTodo(todo) {
      this.$emit('delete-todo', todo);
    },
    showForm(){
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
    completeTodo(todo){
      this.$emit('complete-todo', todo);
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
