<template>
  <div class="clearAllConainer">
    <span class="clearAllBtn"
      v-on:click="clearTodo">Clear All</span>
    
  </div>
</template>

<script>
import { mapMutations } from 'vuex'

export default {
  methods: {
    ...mapMutations({
      clearTodo: 'clearAllItem'
    })
  }
}
</script>

<style scoped>
.clearAllConainer {
  width: 8.5rem;
  height: 50px;
  line-height: 50px;
  background-color: #fff;
  border-radius: 5px;
  margin: 0 auto;
}
.clearAllBtn {
  color: #e20303;
  display: block;
  font-weight: 700;
  cursor: pointer;
}
</style>