<template>
  <div class="rounded-x1 white text-center">
    <div class="txt01">
      <p>Page sign-up</p>
      <h1>Hello {{ name }} </h1>
      <h1>Hello {{ upperName }} </h1>
      <input type="text" :value="name">
      <input v-model="name" type="text">
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      name: 'Athiwat Thawan'
    }
  },
  computed: {
    upperName () {
      return this.name.toUpperCase()
    }
  }
}
</script>
<style>
.txt01{
    color:rgb(21, 79, 240);
}
</style>
