<template>
  <div>
    <b-card id="loginCard" class="scale-in-bl">
      <b-form v-if="show" id="formLogin" @submit="onSubmit" @reset="onReset">
        <svg
          viewBox="0 0 200 200"
          xmlns="http://www.w3.org/2000/svg"
          class="blob"
        >
          <path
            fill="#41B883"
            d="M66.2,-49.1C81.5,-33.5,86.8,-6.2,79.8,15.6C72.7,37.5,53.3,53.9,30.9,65.1C8.5,76.2,-16.9,81.9,-36.2,73.3C-55.5,64.7,-68.8,41.7,-70.8,19.9C-72.8,-2,-63.6,-22.7,-49.9,-37.8C-36.2,-53,-18.1,-62.7,3.6,-65.6C25.4,-68.5,50.8,-64.6,66.2,-49.1Z"
            transform="translate(100 100)"
          />
        </svg>

        <h1 class="text-center mb-3">Login</h1>
        <h2 class="text-center mb-4">Welcome Back</h2>
        <b-img :src="require('@/assets/images/logo.png')" fluid height="50" class="logoLogin mb-4" />
        <b-form-group id="input-group-1" label-for="email">
          <b-form-input
            id="email"
            v-model="form.email"
            class="input"
            type="email"
            placeholder="E-mail"
            required
          ></b-form-input>
        </b-form-group>

        <b-form-group id="input-group-2" label-for="input-2">
          <b-form-input
            id="password"
            v-model="form.name"
            class="input"
            placeholder="Senha"
            type="password"
            required
          ></b-form-input>
        </b-form-group>

        <div class="d-flex justify-content-between flex-wrap">
          <b-form-checkbox value="remember" class="remember"
            >Lembrar senha</b-form-checkbox
          >
          <div>
            <nuxt-link to="/recover" class="forgotPassword">Esqueceu a senha ?</nuxt-link>
          </div>
        </div>

        <div class="d-flex justify-content-center mt-3">
          <b-button type="submit" variant="primary" class="btn-login"
            >Entrar <font-awesome-icon icon="arrow-right" class="arrow"
          /></b-button>
        </div>

        <div class="d-flex justify-content-center mt-3">
          <a href="#">
            <font-awesome-icon icon="arrow-right" class="arrow-btn" />
          </a>
        </div>

        <div class="d-flex justify-content-center flex-wrap mt-4 register">
          <span class="mr-2">Ainda não possui conta ?</span>
          <router-link to="/register" class="createAccount">Criar conta</router-link>
        </div>
      </b-form>
    </b-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        email: '',
        name: '',
        food: null,
        checked: [],
      },
      show: true,
    };
  },
  methods: {
    onSubmit(event) {
      event.preventDefault();
      alert(JSON.stringify(this.form));
    },
    onReset(event) {
      event.preventDefault();
      // Reset our form values
      this.form.email = '';
      this.form.name = '';
      this.form.food = null;
      this.form.checked = [];
      // Trick to reset/clear native browser form validation state
      this.show = false;
      this.$nextTick(() => {
        this.show = true;
      });
    },
  },
};
</script>