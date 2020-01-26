<template>
    <div id="app">
        <h1>разочарование</h1>
        <reg
                v-if="REG_FLAG === false"
                @login-to="loginTo"
                @open-reg="openReg"
        />
        <Logout v-if="REG_FLAG === true"
                @log-out="logOut"
        />
        <WindowReg
                v-if="SUCCESS_FLAG"
                @success-reg="successReg"
        />
        <PostEdit
                v-if="EDIT_FLAG"
                @close-edit="closeEdit"
        />
        <ListBlog
                v-bind:REG_FLAG="REG_FLAG"
                @edit-post="editPost"
        />
    </div>
</template>

<script>
    import reg from "@/components/reg";
    import logout from "@/components/Logout";
    import listBlog from "@/components/ListBlog";
    import windowReg from "@/components/WindowReg";
    import PostEdit from "@/components/PostEdit";

    export default {
        name: 'app',
        data() {
            return {
                REG_FLAG: false,
                EDIT_FLAG: false,
                SUCCESS_FLAG: false
            }
        },
        methods: {
            loginTo() {
                this.REG_FLAG = true;
            },
            openReg() {
                this.SUCCESS_FLAG = true;
            },
            logOut() {
                this.REG_FLAG = false;
            },
            successReg() {
                this.SUCCESS_FLAG = false;
            },
            editPost() {
                this.EDIT_FLAG = true;
            },
            closeEdit() {
                this.EDIT_FLAG = false;
            }
        },
        components: {
            reg: reg,
            ListBlog: listBlog,
            Logout: logout,
            PostEdit: PostEdit,
            WindowReg: windowReg
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 15px;
    }
</style>
