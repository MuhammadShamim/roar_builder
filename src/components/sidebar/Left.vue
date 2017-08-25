<template>
    <div id="sidepanel">
            <div id="profile" v-bind:class="{ expanded: brand.expanded }">
                <div class="wrap">
                    <img @click="expandStatusOptions" id="profile-img" src="../../assets/lion_green.png" v-bind:class="brand.status" alt="" />
                    <p class="brand-name">{{brand.name}}</p>
                    <p class="brand-version">{{brand.version}}</p>
                    <i @click="expandBrand" class="fa fa-chevron-down expand-button" aria-hidden="true"></i>
                    <div id="status-options" v-bind:class="{ active: brand.statusOptions }">
                        <ul>
                            <li @click="setStatus('online')" id="status-online" class="active"><span class="status-circle"></span> <p>Online</p></li>
                            <li @click="setStatus('away')" id="status-away"><span class="status-circle"></span> <p>Away</p></li>
                            <li @click="setStatus('busy')" id="status-busy"><span class="status-circle"></span> <p>Busy</p></li>
                            <li @click="setStatus('offline')" id="status-offline"><span class="status-circle"></span> <p>Offline</p></li>
                        </ul>
                    </div>
                    <div id="expanded">
                        <div v-if="admin" id="cms">
                            <label for="twitter"><i class="fa fa-facebook fa-fw" aria-hidden="true"></i></label>
                            <input name="twitter" type="text" value="mikeross" />
                            <label for="twitter"><i class="fa fa-twitter fa-fw" aria-hidden="true"></i></label>
                            <input name="twitter" type="text" value="ross81" />
                            <label for="twitter"><i class="fa fa-instagram fa-fw" aria-hidden="true"></i></label>
                            <input name="twitter" type="text" value="mike.ross" />
                        </div>
                        <div v-else>Access Denied</div>
                    </div>
                </div>
            </div>
            <div id="search">
                <label for=""><i class="fa fa-search" aria-hidden="true"></i></label>
                <input type="text" placeholder="Search services..." />
            </div>
            <div id="contacts">
                <ul>
                    <li v-for="contact in contacts" class="contact" v-bind:class="{ active: contact.active }">
                        <div class="wrap">
                            <span class="contact-status" v-bind:class="contact.status"></span>
                            <img :src="contact.image" alt="" />
                            <div class="meta">
                                <p class="name">{{ contact.name }}</p>
                                <p class="preview">{{ contact.preview }}</p>
                            </div>
                        </div>
                    </li>
                </ul>
            </div>
            <div id="bottom-bar">
                <button id="addcontact"><i class="fa fa-user-plus fa-fw" aria-hidden="true"></i> <span>Add contact</span></button>
                <button id="settings"><i class="fa fa-cog fa-fw" aria-hidden="true"></i> <span>Settings</span></button>
            </div>
        </div>
</template>

<script>
    export default {
        data () {
            return {
                admin: true,
                contacts: [
                    {
                        status: 'online',
                        active: true,
                        name: 'Wexnet',
                        image: './dist/wexnet.png',
                        preview:'Hello Wexnet!'
                    },{
                        status: 'busy',
                        active: false,
                        name: 'Lion 1.0.0',
                        image: './dist/lion_green.png',
                        preview: 'Wrong. You take the gun, or you pull out a bigger one. Or, you call their bluff. Or, you do any one of a hundred and forty six other things.'
                    },{
                        status: 'away',
                        active: false,
                        name: 'Akhtar Shamim',
                        image: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/926516/profile/profile-80.jpg?1',
                        preview: 'I was thinking that we could have chicken tonight, sounds good?'
                    },{
                        status: 'online',
                        active: false,
                        name: 'Donna Paulsen',
                        image: 'http://emilcarlsson.se/assets/donnapaulsen.png',
                        preview: 'Mike, I know everything! Im Donna..'
                    }
                ]
            }
        },
        props:['brand'],
        methods: {
            expandBrand() {
                this.brand.expanded = !this.brand.expanded;
            },
            expandStatusOptions(){
                this.brand.statusOptions = !this.brand.statusOptions;
//                this.brand.status = (this.brand.status == "online") ? "away" : "online";
            },
            setStatus(status){
                this.brand.status = status;
                this.brand.statusOptions = !this.brand.statusOptions;
            }
        }
    }
</script>

<style>
</style>