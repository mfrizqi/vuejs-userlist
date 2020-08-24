<template>
    <div class="modal is-active">
        <div class="modal-background"></div>
        <div class="modal-card">
            <header class="modal-card-head">
            <p class="modal-card-title is-bold">Edit User</p>
            <button class="delete" aria-label="close" @click="closeModal()"></button>
            </header>

            <section class="modal-card-body">
            <!-- Content ... -->

            {{this.uname}}
                <!-- USER:ID -->
                <b-input type="hidden" :value="userChange.id"></b-input>

                <!-- USER:Name -->
                <b-field label="Name">
                    <b-input v-model="name" :placeholder="userChange.name"></b-input>
                </b-field>

                <!-- USER:username -->
                <b-field label="Username">
                    <b-input  v-model="username" :placeholder="userChange.username" maxlength="30"></b-input>
                </b-field>

                <!-- USER:email -->
                <b-field label="Email">
                    <b-input type="email"
                        v-model="email"
                        :placeholder="userChange.email"
                        maxlength="30">
                    </b-input>
                </b-field>

                <!-- USER:division -->
                <b-field label="Division">
                    <b-select :placeholder="userChange.division" v-model="division">
                        <option value="Front-End Developer">Front-End Developer</option>
                        <option value="Back-End Developer">Back-End Developer</option>
                        <option value="Project Manager">Project Manager</option>
                        <option value="UI/UX Designer">UI/UX Designer</option>
                    </b-select>
                </b-field>
  
            </section>

            <footer class="modal-card-foot">
                <button class="button is-success" @click="updateUser()">Save changes</button>
                <button class="button" @click="closeModal()">Cancel</button>
            </footer>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ModalUser',
    props : 
    [   
        'userChange'
    ],
    data(){
        return{
            uname : this.userChange.name
        }
    },
    methods: {
        updateUser(){
            const upUser = {
                id : this.userChange.id,
                name : this.name,
                username : this.username,
                email : this.email,
                division: this.division
            }

            this.$emit('update-user', upUser)
            this.$emit('close')
        },
        closeModal(){
            this.$emit('close')
        }
    },
}

</script>

<style>

</style>