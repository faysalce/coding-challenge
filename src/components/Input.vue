<template>
  <form  @submit.prevent="onSubmit">
    <input type="text"  name="todoText" id="new-todo-input" v-model.lazy.trim="text" />
    <button type="submit" :disabled="isAddTodoButtonDisable">Add</button>
  </form>
</template>

<script type="ts">
export default {
  methods: {
    onSubmit() {
      if(this.text === "") {
        return;
      }
      this.$emit('todo-added', this.text);
      this.text = "";
    }
  },
  props:{
    totalItems:Number
  },
  data() {
    return {
      text: ""
    };
  },
 
  setup() {
    // setup component
    return {};
  },
  computed: {
    isAddTodoButtonDisable() {
     return this.totalItems>9;
    }
  }
};
</script>
