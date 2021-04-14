<template>
   <div class="container">
      <h1>Login</h1>
      <form @submit.prevent="login">
         <div class="form-group">
            <label for="email">E-mail</label>
            <input type="email" id="email" v-model="usuario.email">
         </div>
         <div class="form-group">
            <label for="senha">Senha</label>
            <input type="password" id="senha" v-model="usuario.senha">
         </div>

         <button class="btn btn-primary" type="submit">
            Logar
         </button>
         <router-link :to="{ name: 'novo.usuario' }">
            Cadastre-se aqui
         </router-link>
      </form>
   </div> 
</template>

<script>
    export default {
        name: "Login",

       data() {
          return {
             usuario: {
                email: '',
                senha: ''
             }
          }
       },

       methods: {
          login() {
             this.$http.post('auth/login', this.usuario)
             .then(  ({data}) => {
                 localStorage.setItem('token', data.access_token);
                 this.$router.push({name: 'gerentes'})
             })
          }
       },
    }
</script>

<style scoped>

</style>
