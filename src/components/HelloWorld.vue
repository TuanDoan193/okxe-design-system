<template>
  <div class="hello">
    <OkxeButton  label="Tesst" />
    <h2>Radio Button</h2>
    <OkxeRadioButton :value="radioValue" :options="radioOptions" />
  </div>
</template>

<script>
import OkxeButton from './OkxeButton.vue'
import OkxeRadioButton from './OkxeRadioButton.vue'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: { OkxeButton, OkxeRadioButton },
  data() {
    return {
        radioValue: 1,
        radioOptions: [
            {
                text: 'Option 1',
                value: 1
            },
            {
                text: 'Option 2',
                value: 2
            },
            {
                text: 'Option 3',
                value: 3
            }
        ]
    }
  }
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
