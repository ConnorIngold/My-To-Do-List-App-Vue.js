<template>
  <div class="todo-input">
    <input type="text" v-model="text">
    <button class='btn-primary' v-on:click='addTodo' v-on:submit='addTodo'>Submit</button>
    <!-- On click excute the addTodo function insde methods  -->
  </div>
</template>
<script>
export default {
  name: "todo-input",
  // sets the name of the component equal to todo-input
  data(){
    // data is interal to the component cant access it from the outside
    return {
      text: ""
      // text is equal to v-model="text"
    };
  },
  methods: {
    // all the functions which are exclusive to the component
    addTodo() {
      this.$emit('todo:add', this.text)
    // $emit creates a new type of custom event listener
    // I have the event todo:add and mapped the input to it

    }
  }
}
</script>
<style scoped>
.todo-input-wrapper {
  margin-bottom: 20px;
}
.btn {
  outline: none;
  box-shadow: none;
  border-width: 2px;
  border-radius: 3px;
  border-style: solid;
  padding: 8px;
}

.btn-primary {
  color: rgba(73, 204, 249, 1.0);
  border-color: rgba(73, 204, 249, 1.0);
  background-color: transparent;
}

input {
  width: 80%;
  border: none;
  border-top: 2px solid rgba(73, 204, 249, 1.0);
  border-bottom: 2px solid rgba(73, 204, 249, 1.0);
  margin-right: 10px;
  padding: 5px;
  line-height: 17px;
}

input:focus {
  outline: none;
  border: none;
  border-top: 2px solid rgba(73, 204, 249, 1.0);
  border-bottom: 2px solid rgba(73, 204, 249, 1.0);
}
</style>