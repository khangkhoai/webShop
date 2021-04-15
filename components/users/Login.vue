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
              />
            </div>
          </form>
          <div class="d-flex justify-content-between align-items-center mb-2">
            <div class="form-check pl-0 mb-3">
              <input
                type="checkbox"
                class="form-check-input filled-in"
                id="new"
              />
              <label
                class="form-check-label small text-uppercase card-link-secondary"
                for="new"
                >Remember me</label
              >
            </div>
            <p><a href="">Forgot password?</a></p>
          </div>
          <div class="text-center pb-2">
            <button
              type="submit"
              class="btn btn-primary mb-4 waves-effect waves-light"
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
export default {}
</script>

<style></style>
