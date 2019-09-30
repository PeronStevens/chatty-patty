<template>
    <div class="chat-app" >
        <Conversation :contact="selectedContact" :messages="messages" />
        <ContactList :contacts="contacts" @selected="startConversation" />
    </div>
</template>

<script>
    import Conversation from './Conversation';
    import ContactList from './ContactList';

    export default {
        props: {
            user: {
                typ: Object,
                required: true
            }
        },
        data: function() {
            return {
                selectedContact: null,
                messages:[],
                contacts: []
            };
        },
        mounted() {
            console.log('Component mounted.')
            console.log(this.user);
            axios.get('/contacts')            
            .then((res) => {
                console.log(res.data);
                this.contacts = res.data;
            })
        },
        components: {Conversation, ContactList},
        methods: {
            startConversation(contact) {
                axios.get('/conversation/' + contact.id)
                .then((res) => {
                    this.messages = res.data;
                    this.selectedContact = contact;
                })
            }
        }
    }
</script>

<style lang="scss" scoped>
    .chat-app {
        display: flex;
    }
</style>
