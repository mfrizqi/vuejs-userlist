<template>
  <div>
    <ModalUser v-show="isModalActive" @close="isModalActive = false" v-bind:userChange="userChange" v-on:update-user="updateUser"/>

    <div v-if="users.length == 0">
        <section class="hero is-primary">
            <div class="hero-body">
                <div class="container has-text-centered has-text-weight-medium">
                    <h1 class="title">
                        There is no user
                    </h1>
                </div>
            </div>
        </section>
    </div>

    <div v-for="user in users" :key="user.id">
        <div class="card mb-4 pb-4">
            <div class="card-content">
                <div class="media">
                    <div class="media-content">
                        <div class="content">
                            <p class="title is-4">
                                {{user.name}}
                            </p>
                            <p class="subtitle is-5">
                                {{user.division}}
                            </p>
                        </div>
                    </div>
                    <div class="media-right">
                        <p class="has-text-right">
                            @{{user.username}}
                            <br/>
                            {{user.email}}
                        </p>
                        <nav class="level" style="margin-top: 1em">
                            <div class="level-right">
                            </div>
                            <div class="level-left">
                                <a class="level-item">
                                    <section>
                                        <button class="button is-primary"
                                            @click="changeModal(user)">
                                            Edit
                                        </button>
                                    </section>
                                </a>
                                <a class="level-item">
                                    <b-button @click="$emit('del-user', user.id)" class="button is-danger">delete</b-button>
                                </a>
                            </div>
                        </nav>
                    </div>
                </div>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
import ModalUser from './ModalUser'

export default {
    name: 'UserList',
    props:['users'],
    components:{
        ModalUser
    },
    data() {
        return {
            isModalActive : false,
            userChange : null,
        }
    },
    methods:{
        changeModal(user){
            this.isModalActive = true;
            this.userChange = user
        },
        updateUser(updateUser){
            this.$emit('update-user', updateUser)
        }
    }
}
</script>

<style>

.card{
    margin-bottom: 1em;
}

</style>