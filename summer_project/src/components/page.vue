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
    <hr>
    Input form section
    <br>
    <br>
    <form>
      <div class="row">
        <div class="col-3"></div>
        <div class="col-2">
          <div class="form-group">
            <label for="exampleInputEmail1">input 1</label>
            <input type="text" class="form-control" placeholder="Enter value">
          </div>
          <button type="submit" class="btn btn-primary">Submit</button>
        </div>
        <div class="col-2">
          <div class="form-group">
            <label for="exampleInputEmail1">input 2</label>
            <input type="text" class="form-control" placeholder="Enter value">
          </div>
          <button type="submit" class="btn btn-primary">Submit</button>
        </div>
        <div class="col-2">
          <div class="form-group">
            <label for="exampleInputEmail1">input 3</label>
            <input type="text" class="form-control" placeholder="Enter value">
          </div>
          <button type="submit" class="btn btn-primary">Submit</button>
        </div>
        <div class="col-3"></div>
      </div>
      <br>
      <div class="row">
        <div class="col-3"></div>
        <div class="col-2">
          <div class="form-group">
            <label for="exampleInputEmail1">input 4</label>
            <input type="text" class="form-control" placeholder="Enter value">
          </div>
          <button type="submit" class="btn btn-primary">Submit</button>
        </div>
        <div class="col-2">
          <div class="form-group">
            <label for="exampleInputEmail1">input 5</label>
            <input type="text" class="form-control" placeholder="Enter value">
          </div>
          <button type="submit" class="btn btn-primary">Submit</button>
        </div>
        <div class="col-2">
          <div class="form-group">
            <label for="exampleInputEmail1">input 6</label>
            <input type="text" class="form-control" placeholder="Enter value">
          </div>
          <button type="submit" class="btn btn-primary">Submit</button>
        </div>
        <div class="col-3"></div>
      </div>
    </form>    
  </div>
</template>

<script>
export default {
  name: 'Defaultpage',
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
