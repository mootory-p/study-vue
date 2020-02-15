<template>
  <section>

    <transition-group name="list" tag="ul">
      <li v-for="(todoItem, index) in propsdata" :key="todoItem">
        <p><i class="checkBtn fas fa-check" aria-hidden="true"></i>{{todoItem}}</p>
        <span class="removeBtn" type="button" @click="editTodo(todoItem, index)"><i class="fas fa-edit" aria-hidden="true"></i></span>
        <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)"><i class="fas fa-trash-alt" aria-hidden="true"></i></span>
      </li>
    </transition-group>

  </section>
</template>

<script>
  export default {
    props: ['propsdata'],

    methods: {
      removeTodo(todoItem, index) {
        this.$emit('removeTodo', todoItem, index);
      }
    }

  }

</script>
<style scoped>
  .list-enter-active,
  .list-leave-active {
    transition: all 0.5s;
  }

  .list-enter {
    opacity: 0;
    transform: translateY(20px);
  }

  .list-leave-to {
    opacity: 0;
    transform: translateY(-20px);
  }

</style>

<style>
  ul {
    list-style: none;
    margin: 0;
    padding: 10px 5px;
  }

  li {
    display: flex;
    align-content: center;
    height: 40px;
    line-height: 40px;
    font-size: 15px;
    border-bottom: 1px solid #ccc;
  }

  li p {
    flex: auto;
  }

  .checkBtn {
    color: forestgreen;
    font-size: 12px;
    line-height: 40px;
    margin-right: 8px;
  }

  .removeBtn {
    color: #999;
    font-size: 12px;
    line-height: 40px;
    width: 30px;
    height: 40px;
    text-align: center;
  }

</style>
