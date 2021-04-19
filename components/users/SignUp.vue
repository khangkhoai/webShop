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
                
              </div>
              <div class="md-form md-outline mt-0">
                <label data-error="wrong" data-success="right" for="defaultForm-pass2">Your password</label>
                <input type="password" id="defaultForm-pass2" class="form-control" v-model="dataForm.password">
                
                <small id="materialRegisterFormPasswordHelpBlock" class="form-text text-muted mb-4">
                  At least 8 characters and 1 digit
                </small>
              </div>
              <div class="md-form md-outline mt-0">
                <label data-error="wrong" data-success="right" for="defaultForm-email2">Name</label>
                <input type="name" id="defaultForm-email2" class="form-control" v-model="dataForm.name">
                
              </div>
              <div class="md-form md-outline">
                <label for="materialRegisterFormPhone">Phone number</label>
                <input type="number" id="materialRegisterFormPhone" class="form-control" aria-describedby="materialRegisterFormPhoneHelpBlock" v-model="dataForm.phone">
                
                <small id="materialRegisterFormPhoneHelpBlock" class="form-text text-muted mb-3">
                  Optional - for two step authentication
                </small>
              </div>
               <div class="md-form md-outline mt-0">
                <label data-error="wrong" data-success="right" for="defaultForm-email2">Address</label>
                <input type="address" id="defaultForm-email2" class="form-control" v-model="dataForm.address">
                
              </div>
            </form>      
            <div class="text-center mb-2">
        
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
       
      },
      
    };
  },
  props: {
    title: ""
  },
  methods: {
    addProduct() {
      axios
        .post("http://127.0.0.1:8000/api/customer/", this.dataForm )
        .then(res => {
          this.$router.push("/product");
        
        });
    },
  }
}
</script>

<style>

</style>