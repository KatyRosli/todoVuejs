<template>
  <div class='container'>
    <h2>My Vue TodoApp</h2>

    <div>
      <input type='text' placeholder='Enter task'>
      <button>SUBMIT</button>
    </div>

    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<style scoped>
</style>