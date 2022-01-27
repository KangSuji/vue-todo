<template>
  <div class="inputBox shadow" v-on:click="focus">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
    <span class="addContainer" v-on:click="addTodo">
      <i class="fas fa-plus addBtn"></i>
    </span>
    <Modal v-if="showModal" @close="showModal = false">
      <!--
      you can use custom content here to overwrite
      default content
      -->
      <h3 slot="header">
        경고!
        <i class="fas fa-times closeModalBtn" @click="showModal = false"></i>
      </h3>
      <div slot="body">무언가를 입력하세요!</div>
      <h5 slot="footer"> &copy; copy right </h5>
    </Modal>
  </div>
</template>

<script>
import Modal from './common/Modal.vue'

export default {
  data: function () {
    return {
      newTodoItem : '',
      showModal: false
    }
  },
  methods: {
    addTodo: function () {
      if(this.newTodoItem !== ''){
        this.$emit('addTodoItem', this.newTodoItem)
        this.clearInput();
      } else {
        this.showModal = !this.showModal;
      }
    },
    clearInput: function () {
      this.newTodoItem = '';
    },
    focus: function() {
      document.querySelector('input').focus();
    }
  },
  components: {
    Modal
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
.closeModalBtn {
  color: #42b983;
}

</style>