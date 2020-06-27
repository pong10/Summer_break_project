<template>
  <div>
    <form class="form-signin">
      <img class="mb-4" src="@/assets/star.png" alt="Star" width="100" height="100">
      <h1 class="h3 mb-3 font-weight-normal">Please sign in</h1>
      <div class="row">
        <div class=col-4></div>
        <div class="col-4">
          <input type="email" id="inputEmail" class="form-control" placeholder="Username" required autofocus>
          <div style="padding-top: 10px;"></div>
          <input type="password" id="inputPassword" class="form-control" placeholder="Password" required>
          <br>
          <button class="btn btn-sm btn-primary btn-block" type="submit">Sign in</button>
        </div>
        <div class="col-4"></div>
      </div>
    </form>
    <form>
      <div class="form-group">
        <label for="exampleInputEmail1">Email address</label>
        <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">
        <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
      </div>
      <div class="form-group">
        <label for="exampleInputPassword1">Password</label>
        <input type="password" class="form-control" id="exampleInputPassword1" placeholder="Password">
      </div>
      <div class="form-group form-check">
        <input type="checkbox" class="form-check-input" id="exampleCheck1">
        <label class="form-check-label" for="exampleCheck1">Check me out</label>
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
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
