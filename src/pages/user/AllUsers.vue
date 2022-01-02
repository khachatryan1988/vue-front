<template>
  <div class="container">
    <div class="row">
      <div class="col-md-8 col-md-offset-2">
        <div class="panel panel-default">
          <h3 class="panel-heading">List of users</h3>
          <div class="panel-body">
            <table class="table">
              <thead>
              <tr>
                <th>ID</th>
                <th>Name</th>
                <th>Email</th>

              </tr>
              </thead>
              <tbody>
              <tr v-for="user in users">
                <td>{{ user.id }}</td>
                <td>{{ user.name }}</td>
                <td>{{ user.email }}</td>
                <td>




                </td>
              </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {

      users: {
        name: '',
        email: '',
      },
    }
  },
  mounted() {

    this.getUsers();
  },

  methods: {

    getUsers() {
      return new Promise((resolve, reject) => {
        axios.get('/users')
          .then(res => {
            if (res.status === 200) {
              this.users = res.data
              resolve(true)
            }
          })
          .catch(error => {
            reject(error)
          })
      })


    }
  }
}
</script>

<style scoped>

</style>
