<template>
    <div class="conversation" >
        <h1> {{ contact ? contact.name : 'Select a Contact' }} </h1>
        <MessageFeed :contact="contact" :messages="messages" />
        <MessageComposer @send="sendMessage" />
    </div>
</template>

<script>

import MessageComposer from './MessageComposer';
import MessageFeed from './MessageFeed';

export default {
    props: {
        contact: {
            type: Object,
            default: null
        },

        messages: {
            type: Array,
            default: []
        }
    },
    methods: {
        sendMessage(text) {
            console.log(text);

        }
    },
    components: {MessageComposer, MessageFeed}
}
</script>

<style lang="scss" scoped>
    .conversation {
        flex: 5;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        max-height: 100vh;
        
        h1 {
            font-size: 20px;
            padding: 10px;
            margin: 0px;
            border-bottom: 1px solid;
        }
    }
</style>