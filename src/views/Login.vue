<template>
  <div class="login">
    <h3>Sign In</h3>
    <input v-model="email" type="text" placeholder="Email" />
    <input v-model="password" type="password" placeholder="Password" />
    <br />
    <button @click="login">Login</button>
    <p>
      You don't have an account ? You can
      <router-link to="/sign-up">create one</router-link>
    </p>
  </div>
</template>

<script>
import firebase from 'firebase';

export default {
  name: 'login',
  data() {
    return {
      email: '',
      password: ''
    };
  },
  methods: {
    login() {
      firebase
        .auth()
        .signInWithEmailAndPassword(this.email, this.password)
        .then(
          () => {
            this.$router.replace('home');
          },
          err => {
            alert('Ooops' + err.message);
          }
        );
    }
  }
};
</script>

<style scoped>
.login {
  margin-top: 40px;
}
input {
  margin: 10px 0;
  width: 20%;
  padding: 15px;
}
button {
  margin-top: 20px;
  cursor: pointer;
}
p {
  margin-top: 40px;
  font-size: 13px;
}
p a {
  text-decoration: underline;
  cursor: pointer;
}
</style>
