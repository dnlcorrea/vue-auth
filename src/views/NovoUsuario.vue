<template>
    <div class="container">
        <h1>Novo Usuário</h1>
        <form action="" @submit.prevent="submit">
            <div class="form-group">
                <label for="nome">Nome</label>
                <input v-model="usuario.nome" type="text" id="nome" name="nome" class="form-control"/>
            </div>
            <div class="form-group">
                <label for="email">E-mail</label>
                <input v-model="usuario.email" type="text" id="email" name="email" class="form-control"/>
            </div>
            <div class="form-group">
                <label for="senha">Senha</label>
                <input v-model="usuario.senha" type="password" id="senha" name="senha" class="form-control"/>
            </div>

            <button class="btn btn-primary" type="submit">
                Salvar
            </button>
        </form>
    </div>
</template>

<script>
    export default {
        name: "NovoUsuario",
        data: () => ({
            usuario: {
                nome: '',
                email: '',
                senha: ''
            },
        }),

        methods: {
            submit() {
                this.$http.post('http://localhost:8000/auth/register', this.usuario)
                    .then(response => {
                        console.log(response)
                        this.$router.push({name: 'login'})
                    })
                    .catch(error => {
                        console.log(error)
                    });
            }
        },
    }
</script>

<style scoped>

</style>