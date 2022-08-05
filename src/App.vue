<template>
    <div id="app">
        <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
        <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
        <!-- Button -->
        <h2>Button</h2>
        <div class="default-style">
          <span>Button default</span>
          <okxe-button label="Default" @click="clickFunc">
            <template #icon>
              <v-img src="/images/badge_facebook.png" width="16" height="16"></v-img>
            </template>
          </okxe-button>
        </div>
        <div class="default-style">
          <span>Large Button</span>
          <okxe-button label="Large" backgroundColor="gray" large width="300">
            <template #icon>
              <v-img src="/images/badge_facebook.png" width="16" height="16"></v-img>
            </template>
          </okxe-button>
        </div>
        <div class="default-style">
          <span>Medium button</span>
          <okxe-button label="Meium" backgroundColor="white" medium>
            <template #icon>
              <v-img src="/images/badge_facebook.png" width="16" height="16"></v-img>
            </template>
          </okxe-button>
        </div>
        <div class="default-style">
          <span>Small Button</span>
          <okxe-button label="Small" backgroundColor="red" small width="107" borderRadius="16">
          </okxe-button>
        </div>
        <div class="default-style">
          <span>Disable Button</span>
          <okxe-button
              colorText="black"
              disabled
              border-radius="8"
              width="200px"
              medium
              label="disable button"
          />
        </div>

        <!-- circle -->
         <okxe-button
            background-color="white"
            circleButton="large"
        >
            <template #icon>
               <v-img src="/images/badge_facebook.png" width="16" height="16"></v-img>
            </template>
        </okxe-button>
        <okxe-button
            background-color="white"
            circleButton="medium"
        >
            <template #icon>
               <v-img src="/images/badge_facebook.png" width="16" height="16"></v-img>
            </template>
        </okxe-button>

        <okxe-button
            background-color="rgba(18, 22, 23, 0.5)"
            circleButton="small"
        >
            <template #icon>
               <v-img src="/images/badge_facebook.png" width="16" height="16"></v-img>
            </template>
        </okxe-button>
        <v-divider></v-divider>
        <!-- okxe toggle -->
        <h2>Okxe Toggle</h2>
        <okxe-toggle
          v-model="checkbox"
        >
          <span>
            Test checkbox
          </span>
        </okxe-toggle>
        <!-- end okxe toggle -->
        <okxe-button
            bottom-fixed
            border-radiu="0"
            backgroundColor="#00BCC3"
            large
            label="Xác Nhận (Bottom button)"
        >
        </okxe-button>
    </div>
</template>

<script>
import OkxeButton from './components/OkxeButton.vue'
import OkxeToggle from './components/OkxeToggle.vue'
export default {
  name: 'App',
  components: {
    // HelloWorld
    OkxeButton,
    OkxeToggle
  },
  data() {
    return {
      checkbox: false,
    }
  },
  methods: {
    clickFunc() {
      alert("click in default button")
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
<style lang="sass" scoped>
.default-style
    display: flex
    justify-content: center
    align-items: baseline

</style>
