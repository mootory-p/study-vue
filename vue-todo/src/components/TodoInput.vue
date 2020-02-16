<template>
  <div>
    <input class="intext" type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo">

    <span class="addContainer" v-on:click="addTodo">
      <i class="addBtn fas fa-plus" aria-hidden="true"></i>
    </span>
    <modal v-if="showModal" @close="showModal = false">
      <h3 slot="header">잠깐!</h3>
      <div slot="footer" >할일을 입력하세요 <i class="closeModalBtn fas fa-times" aria-hidden="true" @click="showModal = false"></i></div>
    </modal>
  </div>

</template>


<script>
  import Modal from './common/Modal.vue'

  export default {
    data() {
      return {
        newTodoItem: '',
        showModal :false
      }
    },
    components:{
      Modal:Modal
    },
    methods: {
      addTodo() {
        if (this.newTodoItem !== "") {
          var value = this.newTodoItem && this.newTodoItem.trim();
          this.$emit('addTodo', value)
          this.clearInput();
        } else {
          this.showModal = !this.showModal;
        }
      },
      clearInput() {
        this.newTodoItem = '';
      }
    },

  }

</script>


<style>
  .intext:focus{outline: none}
  .intext
   {height: 40px; width: calc(100% - 50px); border-radius: 4px 0 0 4px; font-size: 0.9rem;border:1px solid #ccc;padding: 0.3rem;}
  .addContainer { float: right; display: block; width: 50px; height: 40px; border-radius: 0 4px 4px 0; text-align: center;color: #fff; background-color: mediumpurple;}
  .addBtn { line-height: 40px;}
</style>
