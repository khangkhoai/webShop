<template>
  <div class="container" style="margin-top: 35px">
    <div class="row">
      <div class="col-md-6">
        <!--Section: Content-->
        <section class="mb-5">
          <form action="#!">
            <div class="md-form md-outline">
               <label
                data-error="wrong"
                data-success="right"
                for="defaultForm-email1"
                class=""
                >Your email</label
              >
              <input
                type="email"
                id="defaultForm-email1"
                class="form-control"
                v-model="userForm.email"
              />
             
            </div>
            <div class="md-form md-outline">
               <label
                data-error="wrong"
                data-success="right"
                for="defaultForm-pass1"
                class=""
                >Your password</label
              >
              <input
                type="password"
                id="defaultForm-pass1"
                class="form-control"
                v-model="userForm.password"
              />
            </div>
          </form>
          <div class="d-flex justify-content-between align-items-center mb-2">
            <p><a href="">Forgot password?</a></p>
          </div>
          <div class="text-center pb-2">
            <button
              type="submit"
              class="btn btn-primary mb-4 waves-effect waves-light"
              @click="login"
            >
              Sign in
            </button>

            <p>Not a member? <a href="/user/sign-up">Register</a></p>
          </div>
        </section>
        <!--Section: Content-->
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
     
      customerLogin : [],
      userForm: {
        email: "",
        password: "",
        
      },
      err: {},
    };
  },
  methods: {
    login() {
      this.validate();
      axios.post('http://127.0.0.1:8000/api/auth/login-customer/',this.userForm)
       .then((res) => {
          this.customerLogin = res.data
          document.cookie = "id" + "=" + this.customerLogin.id;
          document.cookie = "name" + "=" + this.customerLogin.name;
          console.log(this.customerLogin);
          this.$router.push("/product");  
        })
        
    },
    validate() {
      this.err = {};
      if (this.userForm.email === "") {
        this.err.email = "email không được để trống";
      } else if (this.userForm.password === "") {
        this.err.password = "mật khẩu không được để trống";
      }
    },
    register(){
      this.$router.push('/Register')
    }
  },
}
</script>

<style></style>
