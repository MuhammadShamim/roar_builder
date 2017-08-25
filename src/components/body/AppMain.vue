<template>
    <div class="content">
        <div class="contact-profile">
            <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/926516/profile/profile-80.jpg?1" alt="" />
            <p>Akhtar Shamim</p>
            <div class="social-media">
                <i class="fa fa-facebook" aria-hidden="true"></i>
                <i class="fa fa-twitter" aria-hidden="true"></i>
                <i class="fa fa-instagram" aria-hidden="true"></i>
            </div>
        </div>
        <div class="messages">
            <ul>
                <li v-for="message in messages" v-bind:class="message.status">
                    <img :src="message.image" alt="" />
                    <p>{{message.content}}</p>
                </li>
            </ul>
        </div>
        <div class="message-input">
            <div class="wrap">
                <input v-on:keyup.enter="newMessage" class="input" type="text" placeholder="Start writing new message .." v-model="newMsg">
                <i class="fa fa-paperclip attachment" aria-hidden="true"></i>
                <button @click="newMessage" class="submit"><i class="fa fa-paper-plane" aria-hidden="true"></i></button>
            </div>
        </div>
    </div>

</template>

<script>
    export default{
        data(){
            return {
                newMsg: '',
                messages: [
                    {
                        status: 'replies',
                        image: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/926516/profile/profile-80.jpg?1',
                        content: 'Hey there'
                    },{
                        status: 'sent',
                        image: this.brand.image,
                        content: 'Sup...'
                    }
                ]
            }
        },
        props: ['brand'],
        methods:{
            newMessage(){
                let msg = this.newMsg.trim();
                this.newMsg = '';

                if(!msg){
                    return false;
                }

                if(msg === 'cls'){
                    this.messages = [];
                }

                this.messages.push({
                    status: 'sent',
                    image: this.brand.image,
                    content: msg
                });
                this.newMsg = '';
            }
        }
    }
</script>
