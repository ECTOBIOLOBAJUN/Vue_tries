<template>
    <div class="b-popup">
        <div class="b-popup-content">
            <form @submit.prevent="onSubmit">
                <button type="submit">close</button>
                <textarea v-model="text"> </textarea>
            </form>
        </div>
    </div>
</template>

<script>
    export default {
        name: "PostEdit",
        data() {
            return {
                textId: require('@/data-post.json').idNow,
                text: require('@/data-post.json').posts[require('@/data-post.json').idNow].content
            }
        },
        methods: {
            onSubmit() {
                const post = require('@/data-post.json');
                post.posts[this.textId].content = this.text;
                this.$emit('close-edit');
            }
        },
    }
</script>

<style scoped>

    textarea {
        width: 90%;
        height: 100%;
    }

    .b-popup {
        width: 100%;
        min-height: 100%;
        background-color: rgba(0, 0, 0, 0.5);
        overflow: hidden;
        position: fixed;
    }

    .b-popup .b-popup-content {
        margin: 40px auto 0px auto;
        width: 1000px;
        height: 200px;
        padding: 10px;
        background-color: #ffffff;
        border-radius: 3px;
    }

    .b-popup-content {
        display: flex;
        flex-direction: column;
    }

    button {
        text-align: center;
        font-size: 13px;
        text-decoration: none;
        font-weight: 700;
        padding: 3px 6px;
        background: #eaeef1;
        display: block;
        width: 60px;
        margin: 20px auto;
        background-image: linear-gradient(rgba(0, 0, 0, 0), rgba(0, 0, 0, .1));
        border-radius: 3px;
        color: rgba(0, 0, 0, .6);
        text-shadow: 0 1px 1px rgba(255, 255, 255, .7);
        box-shadow: 0 0 0 1px rgba(0, 0, 0, .2), 0 1px 2px rgba(0, 0, 0, .2), inset 0 1px 2px rgba(255, 255, 255, .7);
    }

    button:hover, button.hover {
        background: #fff;
    }

    button:active, button.active {
        background: #d0d3d6;
        background-image: linear-gradient(rgba(0, 0, 0, .1), rgba(0, 0, 0, 0));
        box-shadow: inset 0 0 2px rgba(0, 0, 0, .2), inset 0 2px 5px rgba(0, 0, 0, .2), 0 1px rgba(255, 255, 255, .2);
    }
</style>