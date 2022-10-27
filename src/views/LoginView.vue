<template>
  <div class="container mt-5">
    <div class="row justify-content-md-center">
      <div class="col-md-auto mt-5 login-container rounded">
        <h1 class="text-center mt-5">Login</h1>
        <h3 class="mt-3 mb-3 para">Sign in to Patient Care</h3>
        <div class="btn-group mb-3" data-toggle="buttons">
          <label class="btn btn-warning active">
            <input
              v-model="removelines"
              name="removelines"
              type="radio"
              class="cheker"
              autocomplete="off"
              v-bind:value="'doctor'"
              checked
            />
            Doctor
          </label>
          <label class="btn btn-warning">
            <input
              v-model="removelines"
              name="removelines"
              type="radio"
              class="cheker"
              v-bind:value="'patient'"
            />
            Patient
          </label>
        </div>
        <form @submit.prevent="validate">
          <label>Username</label>
          <div class="input-group mb-3">
            <input
              type="text"
              class="form-control"
              placeholder="Username"
              aria-label="Username"
              aria-describedby="basic-addon1"
              v-model="username"
            />
          </div>
          <label>Password</label>
          <div class="input-group mb-3">
            <input
              type="password"
              class="form-control"
              placeholder="Recipient's password"
              aria-label="Recipient's password"
              aria-describedby="basic-addon2"
              v-model="password"
            />
          </div>
          <div class="d-grid gap-2 mb-5">
            <button
              class="btn btn-danger"
              type="button"
              @click.enter="validate"
            >
              Button
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: "",
      password: "",
      removelines: "patient",
    };
  },
  methods: {
    validate() {
      if(this.removelines === "patient"){
        localStorage.setItem("patientName", this.username);
        localStorage.setItem("patientStatus", this.removelines);
        console.log(this.removelines)
        this.$router.push("/dashboard")
      } else{
        localStorage.setItem("doctorName", this.username);
        localStorage.setItem("doctorStatus", this.removelines);
        this.$router.push("/dashboard")
        console.log(this.removelines)
      }
    },
  },
};
</script>

<style scoped>
.login-container {
  width: 400px;
  background: #fff;
  box-shadow: rgba(240, 46, 170, 0.4) -5px 5px,
    rgba(240, 46, 170, 0.3) -10px 10px, rgba(240, 46, 170, 0.2) -15px 15px,
    rgba(240, 46, 170, 0.1) -20px 20px, rgba(240, 46, 170, 0.05) -25px 25px;
}

.para {
  font-style: normal;
  font-weight: 400;
  font-size: 24px;
  line-height: 29px;
  color: #0d0c22;
}

label {
  font-style: normal;
  font-weight: 400;
  font-size: 15px;
  line-height: 24px;
  display: block;

  color: #0d0c22;
}

input {
  display: block;
}
</style>
