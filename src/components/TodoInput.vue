<template>
  <div class="inputBox shadow" v-on:click="focus">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
    <span class="addContainer" v-on:click="addTodo">
      <i class="fas fa-plus addBtn"></i>
    </span>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      newTodoItem : ''
    }
  },
  methods: {
    addTodo: function () {
      if(this.newTodoItem !== ''){
        this.$emit('addTodoItem', this.newTodoItem)
        this.clearInput();
      }
    },
    clearInput: function () {
      this.newTodoItem = '';
    },
    focus: function() {
      document.querySelector('input').focus();
    }
  }
}
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background-color: #fff;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
  position: relative;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
  position: absolute;
  left: 0.5rem;
  top: 33%;
  width: 70%;

}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478fb, #8763fb);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: #fff;
  vertical-align: middle;
  cursor: pointer;
}


</style>