<template>
  <div>
    <div v-if="notlogin === 'no'">
      <h1>Welcome: {{username}}</h1>
      <button v-on:click="logout" class="btn btn-lg btn-danger" type="submit">Sign Out</button>
    </div>
    <form class="form-signin" v-if="notlogin === 'yes'">
      <img class="mb-4" src="@/assets/star.png" alt="Star" width="100" height="100">
      <h1 class="h3 mb-3 font-weight-normal">Please sign in</h1>
      <div class="row">
        <div class=col-4></div>
        <div class="col-4">
          <input type="text" id="inputEmail" class="form-control" placeholder="Username" v-model='username' required autofocus>
          <div style="padding-top: 10px;"></div>
          <input type="password" id="inputPassword" class="form-control" placeholder="Password" v-model='password' required>
          <br>
          <button v-on:click="login" class="btn btn-sm btn-primary btn-block" type="button">Sign in</button>
        </div>
        <div class="col-4"></div>
      </div>
    </form>
    <hr>
    Input form section
    <br>
    <br>
    <p v-if="notlogin === 'yes'" class="text-secondary">-- Please login to change configuration --</p>
    <form v-if="notlogin === 'no'">
      <h1>Current Temperature: {{init_temp}}</h1>
      <br>
      <div class="row" v-for='index in threshold_count' :key="index" >
        <div class="col-lg-2 col-md-1"></div>
        <div class="col-lg-8 col-md-10 col-sm-12">
          <div class="form-group">
            <span>Current </span><label style="text-decoration: underline;text-transform:capitalize;"> {{threshold_name[index-1]}}</label><span> value = {{threshold_data[index-1]}}</span>
          </div>
          <!-- <hr class="new1"> -->
        </div>
        <div class="col-lg-2 col-md-1"></div>
      </div>
      <hr>
      <br>
      <h1>Edit Threshold</h1>
      <div class="row">
        <div class="col-lg-2 col-md-1"></div>
        <div class="col-lg-8 col-md-10 col-sm-12">
          <div class="input-group mb-3">
            <select name="Option" id="section" v-model="edit_threshold_name">
              <option v-for='index in threshold_count' :key="index" :value="threshold_name[index-1]">
                {{threshold_name[index-1]}}
              </option>
            </select>
            <input type="text" class="form-control" placeholder="Enter value" v-model="edit_threshold_data" required>
            <div class="input-group-append">
              <button v-on:click="edit" type="button" class="btn btn-primary">Submit</button>
            </div>
          </div>
        </div>
        <div class="col-lg-2 col-md-1"></div>
      </div> 
    </form>
    <br>
    <br>
    <hr>
    <p class="text-secondary" style="font-size:2vh;">Copyright &copy; 2020 All Rights Reserved by &#128578;</p>    
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Defaultpage',
  props: {
    msg: String
  },
  data () {
    return {
      notlogin: 'yes',
      init_temp: null,
      username: null,
      password: null,
      threshold_count: null,
      threshold_name: [],
      threshold_data: null,
      edit_threshold_data: "",
      edit_threshold_name: "",
      response: null
    }
  },
  async created() {
    this.fetchData()
    this.get_threshold()
    setInterval(this.fetchData, 5000)
    setInterval(this.get_threshold, 5000)
  },
  methods: {
    async edit () {
      let payload = {
        "section_name" : this.edit_threshold_name,
        "section_data" : this.edit_threshold_data
      }
      await axios.post('http://127.0.0.1:5000/api/edit/threshold_data', payload, { headers: { 'Content-Type': 'application/json'}}).then(
        res => {
          this.response = res.data['message']
          window.alert(this.response)
        }
      )
    },
    async login () {
      let payload = {
        "username" : this.username,
        "password" : this.password
      }
      await axios.post('http://127.0.0.1:5000/api/login', payload, { headers: { 'Content-Type': 'application/json'}}).then(
        res => {
          this.notlogin = res.data['message']
        }
      )

      // this.notlogin = 'no'
      // await axios.get('http://127.0.0.1:5000/api/get/temperature').then(
      //   res => {
      //     this.init_temp = res.data['temperature'][0]
      //   }
      // )
    },
    logout () {
      this.notlogin = 'yes'
    },
    async get_threshold () {
      await axios.get('http://127.0.0.1:5000/api/get/data').then(
        res => {
          this.threshold_count = res.data['count']
          this.threshold_name = res.data['name']
          this.threshold_data = res.data['threshold']
        }
      )
    },
    async fetchData () {
      await axios.get('http://127.0.0.1:5000/api/get/temperature').then(
        res => {
          this.init_temp = res.data['temperature'][0]
        }
      )
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
hr.new1 {
  border-top: 1px solid red;
}
</style>
