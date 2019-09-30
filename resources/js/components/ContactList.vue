<template>
    <div class="contact-list" >
        <ul>
            <li v-for="(contact, index) in contacts" :key="contact.id" @click="selectContact(index, contact)" :class="{'selected': index == selected}" >
                <div class="avatar " >
                    <img :src="contact.profile_image" :alt="contact.name">
                </div>
                <div class="contact" >
                    <p class="name">{{ contact.name }}</p>
                    <p class="email">{{ contact.email }}</p>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    data: function() {
        return {
            selected: 0
        }
    },
    props: {
        contacts: {
            type: Array,
            defaults: []
        }
    },
    methods: {
        selectContact(index, contact) {
            this.selected = index;

            this.$emit('selected', contact);
        }
    }
}
</script>

<style lang="scss" scoped>
    .contact-list {
        flex: 2;
        max-height: 100vh;
        overflow: scroll;
        border-left: 1px solid lightgrey;
    }

    ul {
        list-style: none;
        padding: 0;

        li {
            display: flex;
            padding: 2px;
            border-bottom: 1px solid lightgrey;
            height: 80px;
            position: relative;
            cursor: pointer;

            &.selected {
                background: lightgrey;
            }

            .avatar {
                flex: 1;
                display: flex;
                align-items: center;

                img {
                    width: 35px;
                    border-radius: 50%;
                    margin: 0 auto;
                }
            }

            .contact {
                flex: 3;
                font-size: 10px;   
                overflow-y: hidden;
                display: flex;
                flex-direction: column;
                justify-content: center;

                p {
                    margin: 0;

                    p.name {
                        font-weight: bold; 
                    }
                }
            }            
        }
    }



    .avatar img {
        max-width: 100px;
    }
</style>