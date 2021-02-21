<template>
  <div id="app">
    {{ fullName }}
    <strong>Followers: {{followers}} </strong>
    <button v-on:click="followUser"> follow </button> {{ userName }}
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: '_jashanjotsingh',
        firstName: 'Jashanjot',
        lastName: 'Singh',
        email: 'jshn.singh1@gmail.com',
        isAdmin: true
      }
    }
  },
  watch: {
    followers(oldValue, newValue) {
      if (newValue < oldValue) {
        console.log(`${this.userName} has a new follower!`)
      }
    }
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    },
    userName() {
      return `${this.user.username}`;
    }
  },
  methods: {
    followUser() {
      this.followers++
    }
  },
  mounted() {
    this.followUser()
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
  margin-top: 30px;
  margin-left: 30px;
  margin-right: 30px;
  display: flex;
  flex-direction: column;
}
</style>
