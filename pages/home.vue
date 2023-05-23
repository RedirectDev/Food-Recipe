<template>
    <div>
      <li v-for="user of users" :key="user.id">
        <a href="#" @click.prevent="goTo(user)">user {{ user }}</a>
      </li>
    </div>
  </template>
    
    <script>
  export default {
    data() {
      return {
        users: [1, 2, 3],
      }
    },
    methods: {
      goTo(user){
        this.$router.push('/users/'+user)
      }
    },
  }
  </script>
    
    <style>
  </style>