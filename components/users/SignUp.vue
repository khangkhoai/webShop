<template>
  <div class="container">
      <!--Grid row-->
      <div class="row d-flex justify-content-center">
        <!--Grid column-->
        <div class="col-md-6">
          <!--Section: Content-->
          <section class="mt-4 mb-5">
            <form action="#!">
              <div class="md-form md-outline mt-0">
                <label data-error="wrong" data-success="right" for="defaultForm-email2">Your email</label>
                <input type="email" id="defaultForm-email2" class="form-control" v-model="dataForm.email">
                <p v-if="Object.keys(error).length > 0" class="text text-danger">
            {{ error.email }}
          </p>
              </div>
              <div class="md-form md-outline mt-0">
                <label data-error="wrong" data-success="right" for="defaultForm-pass2">Your password</label>
                <input type="password" id="defaultForm-pass2" class="form-control" v-model="dataForm.password">
                <p v-if="Object.keys(error).length > 0" class="text text-danger">
            {{ error.password}}
          </p>
                <small id="materialRegisterFormPasswordHelpBlock" class="form-text text-muted mb-4">
                  At least 8 characters and 1 digit
                </small>
              </div>
              <div class="md-form md-outline mt-0">
                <label data-error="wrong" data-success="right" for="defaultForm-email2">Name</label>
                <input type="name" id="defaultForm-email2" class="form-control" v-model="dataForm.name">
                <p v-if="Object.keys(error).length > 0" class="text text-danger">
            {{ error.name}}
          </p>
              </div>
              <div class="md-form md-outline">
                <label for="materialRegisterFormPhone">Phone number</label>
                <input type="number" id="materialRegisterFormPhone" class="form-control" aria-describedby="materialRegisterFormPhoneHelpBlock" v-model="dataForm.phone">
                 <p v-if="Object.keys(error).length > 0" class="text text-danger">
            {{ error.phone}}
                 </p>
              </div>
               <div class="md-form md-outline mt-0">
                <label data-error="wrong" data-success="right" for="defaultForm-email2">Address</label>
                <input type="address" id="defaultForm-email2" class="form-control" v-model="dataForm.address">
                <p v-if="Object.keys(error).length > 0" class="text text-danger">
            {{ error.address }}
          </p>
              </div>
            </form>      
            <div class="text-center mb-2">
              <br/>
              <button type="submit" class="btn btn-primary mb-4 waves-effect waves-light" @click="addProduct()">Sign Up</button>
              <hr class="mt-4">
              <p>By clicking
                <em>Sign up</em> you agree to our
                <a href="">terms of service</a>
              </p>
            </div>
          </section>
          <!--Section: Content-->
        </div>
        <!--Grid column-->
      </div>
      <!--Grid row-->
    </div>
</template>

<script>
import axios from 'axios'
export default {
   data() {
    return {
      dataForm: {
       email : '',
       password : '',
       name : '',
       phone : '',
       address : ''
      },
      error: {},
    };
  },
  props: {
    title: ""
  },
  methods: {
    addProduct() {
      this.validate();
      console.log(Object.keys(this.error).length);
      if (Object.keys(this.error).length > 0) {
        return this.error;
       
      }
      axios
        .post("http://127.0.0.1:8000/api/customer/", this.dataForm )
        .then(res => {
          this.$router.push("/product");  
        });
    },
    validate() {
      this.error = {};
      console.log(this.dataForm);
      if (this.dataForm.email == "") {
        this.error.email = "email isn't valid";
      } else if (this.dataForm.password == "") {
        this.error.password = "password isn't valid";
      } else if (this.dataForm.name == "") {
        this.error.name = "name isn't valid";
      } else if (this.dataForm.phone == "") {
        this.error.phone = "phone isn't valid";
      } else if (this.dataForm.address== "") {
        this.error.address = "address isn't valid";
      } 
      console.log(this.error);
    },
  }
}
</script>

<style>

</style>