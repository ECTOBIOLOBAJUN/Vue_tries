<template>
        <form @submit.prevent="onSubmit">
            <div class="reg-container">
                <input type="text" placeholder="Введите имя пользователя" v-model="login" >
                <input type="password" placeholder="Введите пароль" v-model="password">
                <button type="submit"> Вход </button>
                <button type="button" v-on:click="$emit('open-reg')">Регистрация</button>
            </div>
        </form>
</template>

<script>
    export default {
        name: "reg",
        data(){
            return {
                login: '',
                password: '',
            }
        },
        methods: {
            onSubmit(){
                const users = require('@/data-user.json');
                var bool = false;
                for(let i = 0; i < users.numberUser; i++){
                    if(bool){
                        break;
                    }
                    if (users.dataUser[i].name === this.login && users.dataUser[i].password === this.password){
                        bool = true;
                    }
                }
                if(bool){
                  this.$emit('login-to');
                  this.login = '';
                  this.password = '';
                }
            },

        }
    }
</script>

<style scoped>
    .reg-container {
        display: flex;
        flex-direction: row;
        margin-right: 10px;
        justify-content: flex-end;
    }


    input {
        width: 200px;
        font-size: 15px;
        padding: 10px;
        border: 1px solid #cecece;
        background: #F6F6f6;
        border-radius: 8px;
        margin-right: 10px;
    }

    button {
        display: inline-block;
        font-family: arial,sans-serif;
        font-size: 11px;
        font-weight: bold;
        color: rgb(68,68,68);
        text-decoration: none;
        user-select: none;
        padding: .2em 1.2em;
        outline: none;
        border: 1px solid rgba(0,0,0,.1);
        border-radius: 2px;
        background: rgb(245,245,245) linear-gradient(#f4f4f4, #f1f1f1);
        transition: all .218s ease 0s;
    }
    button:hover {
        color: rgb(24,24,24);
        border: 1px solid rgb(198,198,198);
        background: #f7f7f7 linear-gradient(#f7f7f7, #f1f1f1);
        box-shadow: 0 1px 2px rgba(0,0,0,.1);
    }
    button:active {
        color: rgb(51,51,51);
        border: 1px solid rgb(204,204,204);
        background: rgb(238,238,238) linear-gradient(rgb(238,238,238), rgb(224,224,224));
        box-shadow: 0 1px 2px rgba(0,0,0,.1) inset;
    }
</style>