<template>
  <div class="main-panel">
    <div class="content-wrapper d-flex align-items-center auth">
      <div class="row w-100">
        <div class="col-lg-4 mx-auto">
          <div class="auth-form-light text-left p-5">
            <div class="navbar-brand brand-logo">
              <img src="assets/img/logo.png" />
            </div>
            <h4>Selamat datang!</h4>
            <h6 class="font-weight-light">Daftar untuk menggunakan aplikasi daily scrum.</h6>
            <form class="pt-3" method="post" action="#" v-on:submit.prevent="Register">
              <div class="form-group">
                <div class="input-group">
                  <div class="input-group-prepend bg-transparent">
                    <span class="input-group-text bg-transparent border-right-0">
                      <i class="mdi mdi-account-outline text-primary"></i>
                    </span>
                  </div>
                  <input
                    type="text"
                    class="form-control form-control-lg border-left-0"
                    id="firstname"
                    name="firstname"
                    v-model="firstname"
                    placeholder="First Name"
                    required
                  />
                </div>
              </div>
              <div class="form-group">
                <div class="input-group">
                  <div class="input-group-prepend bg-transparent">
                    <span class="input-group-text bg-transparent border-right-0">
                      <i class="mdi mdi-account-outline text-primary"></i>
                    </span>
                  </div>
                  <input
                    type="text"
                    class="form-control form-control-lg border-left-0"
                    id="lastname"
                    name="lastname"
                    v-model="lastname"
                    placeholder="Last Name"
                    required
                  />
                </div>
              </div>
              <div class="form-group">
                <div class="input-group">
                  <div class="input-group-prepend bg-transparent">
                    <span class="input-group-text bg-transparent border-right-0">
                      <i class="mdi mdi-message-outline text-primary"></i>
                    </span>
                  </div>
                  <input
                    type="email"
                    class="form-control form-control-lg border-left-0"
                    id="email"
                    name="email"
                    v-model="email"
                    placeholder="E-Mail"
                    required
                  />
                </div>
              </div>
              <div class="form-group">
                <div class="input-group">
                  <div class="input-group-prepend bg-transparent">
                    <span class="input-group-text bg-transparent border-right-0">
                      <i class="mdi mdi-lock-outline text-primary"></i>
                    </span>
                  </div>
                  <input
                    type="password"
                    class="form-control form-control-lg border-left-0"
                    name="password"
                    id="password"
                    v-model="password"
                    placeholder="New Password"
                    required
                  />
                </div>
              </div>
              <div class="form-group">
                <div class="input-group">
                  <div class="input-group-prepend bg-transparent">
                    <span class="input-group-text bg-transparent border-right-0">
                      <i class="mdi mdi-lock-outline text-primary"></i>
                    </span>
                  </div>
                  <input
                    type="password"
                    class="form-control form-control-lg border-left-0"
                    name="password_verify"
                    id="password_verify"
                    v-model="password_confirmation"
                    placeholder="Retype Your New Password"
                    required
                  />
                </div>
              </div>
              <div class="my-3">
                <input
                  type="submit"
                  name="submit"
                  class="btn btn-block btn-primary btn-lg font-weight-medium auth-form-btn"
                  value="REGISTER"
                />
              </div>
            </form>
            <label>Sudah terdaftar?<br/> <a href="/login"> Login </a></label>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        firstname: "",
        lastname: "",
        email: "",
        password: "",
        password_confirmation: ""
      };
    },
    methods: {
      Register: function() {
        let firstname = this.firstname;
        let lastname = this.lastname;
        let email = this.email;
        let password = this.password;
        let password_confirmation = this.password_confirmation;
        this.$store
          .dispatch("register", {
            firstname,
            lastname,
            email,
            password,
            password_confirmation
          })
          .then(() => this.$router.push("/"))
          .catch(err => console.log(err));
      }
    }
  };
</script>