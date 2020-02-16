<template>
   <div class="text-center m-3 clearAll">
     <span class="clearAllBtn" @click="clearTodo">Clear All</span>
    </div>
</template>
<script>
  export default {
    methods: {
      clearTodo() {
        this.$emit('removeAll')
      }
    }
  }
</script>


<style>
  .clearAll span {
    border: 1px solid #ccc;
    padding: 5px 25px;
    cursor: pointer;
    border-radius: 4px;
  }

</style>
