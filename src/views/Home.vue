<template>
  <div class="ion-page">
    <ion-header>
      <ion-toolbar>
        <ion-title>Users List</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <img alt="Vue logo" src="../assets/logo.png">
      <router-link to="/about"><ion-button expand="block" size="small">Go to About Page</ion-button></router-link>         
      <ion-button @click="fetchUsers">Fetch users</ion-button>

      <ion-list v-if="users && users.length">
        <ion-item v-for="user in users" :key="user.id">
          <ion-label>{{user.name}}</ion-label>
        </ion-item>
      </ion-list>
    </ion-content>
  </div>
</template>

<script>
 import axios from 'axios';

 export default {
  name: 'home',
  data () {
    return {
      users: [],
      errors: []
    }
  },
  methods: {
    fetchUsers: function () {
      const baseURI = 'https://jsonplaceholder.typicode.com/users'
      axios.get(baseURI)
      .then((result) => {
        this.users = result.data
      })
    }
  }
};
</script>