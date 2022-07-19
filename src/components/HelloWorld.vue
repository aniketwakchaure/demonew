<template>
<div>
  <h2>User Registration</h2>
  <p>First Name:</p>
  <input v-model="user.firstName" placeholder="" />
  <p>Last Name:</p>
  <input v-model="user.lastName" placeholder="" />
  <button @click="addUser">Add User</button>
  <h3>Your Fullname is: {{fullName}}</h3>
  <table style="width:50%">
    <thead>
      <th>Firstname</th>
      <th>Lastname</th>
    </thead>
    <tbody>
      <tr v-for="(user,index) in userList" :key="index">
        <td>{{user.firstName}}</td>
        <td>{{user.lastName}}</td>
      </tr>
    </tbody>
  </table>
</div>
</template>

<script>
export default{
  name: 'HelloWorld',
  data () {
    return {
      user: {
        firstName: '',
        lastName: ''
      },
      userList: []
    }
  },
  methods: {
    addUser () {
      if (this.user.firstName !== '' && this.user.lastName !== '') {
        this.userList.push(this.user)
        this.user = {
          firstName: '',
          lastName: ''
        }
      } else {
        alert('Name must be filled')
      }
    }
  },
  computed: {
    fullName () {
      return this.user.firstName + ' ' + this.user.lastName
    }
  }
}
</script>
<style>
</style>
