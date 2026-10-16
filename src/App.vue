<template>
  <div id="app">
    <!-- <h1 id="title">{{message}}</h1> -->
    <!-- <test-button></test-button> -->
    <!-- <user-view></user-view> -->
    <!-- <question-view></question-view> -->
    <router-view></router-view>
  </div>
</template>

<script>
// import TestButton from './views/element/TestButton.vue';
// import UserView from './views/element/UserView.vue';

  export default {
    data() {
      return {
        message: 'Hello Vue!',
        // num: 1
      };
    },
    methods: {

      }

  };

</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
}

#inputnumber {
  margin-top: 20px;
}
nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
