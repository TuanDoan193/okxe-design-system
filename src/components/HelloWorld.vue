<template>
  <div class="hello">
    <OkxeButton  label="Tesst" />
  </div>
</template>

<script>
import OkxeButton from './OkxeButton.vue'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: { OkxeButton }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
