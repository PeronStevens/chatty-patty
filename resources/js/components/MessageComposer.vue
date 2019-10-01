<template>
    <textarea v-model="message" @keydown.enter="send" placeholder="Message..." ></textarea>
</template>

<script>
export default {
    data: function() {
        return {
            message: ''
        };
    },
    methods: {
        send(e) {
            e.preventDefault();

            if (this.message == '') {
                return;
            }

            this.$emit('send', this.message);
            this.message = '';
        }
    }
}
</script>

<style lsng="scss" scoped>
    textarea {
        width: 90%;
        margin: 10px;
        resize: none;
        border-radius: 3px;
        border: 1px solid lightgrey;
        padding: 3px;
    }
</style>