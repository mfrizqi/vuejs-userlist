<template>
    <div>
        <section class="hero is-primary">
            <div class="hero-body">
                <div class="container has-text-weight-medium">
                    <h1 class="title">
                        User List Page
                    </h1>
                </div>
            </div>
        </section>

        <section>
            <div class="columns is-centered mt-r">
                <div class="column is-3 addUser">
                    <h2 class="title is-2">Add User</h2>
                    <UserForm v-bind:users="userlist" v-on:new-user="addUser"/>
                </div>
                <div class="column is-1"></div>
                <div class="column is-4 listUser">
                    <h2 class="title is-2">List User : {{userlist.length}} users</h2>
                    <UserList  v-bind:users="userlist" v-on:del-user="deleteUser" v-on:update-user="editUser"/>
                </div>
            </div>
        </section>
    </div>  
</template>

<script>
import UserForm from './UserForm'
import UserList from './UserList'

export default {
    name: 'UserPage',
    components : {
        UserForm,
        UserList,
    },
    data(){
       return{
           showModalUser : false,
           userlist : [
               {
                   id : '1', name : 'John Adam', email: 'johnadam@mail.com', username : 'johnadam80', division : 'Front-End Developer'
               },
               {
                   id : '2', name : 'Brandon Smith', email: 'brandons@mail.com', username : 'bransmith', division : 'Back-End Developer'
               },
               {
                   id : '3', name : 'George Pumpkins', email: 'pump.george@mail.com', username : 'George_pump', division : 'Project Manager'
               },
           ]
       }
   },
   methods:{
       addUser(newUser){
           this.userlist = [...this.userlist, newUser];
           const msg = newUser.name + " successfuly Added!";
           this.$buefy.toast.open({
                         message : msg,
                         type: 'is-success',
                     })
       },
       editUser(updateUser){
           
           let oldname = null;
           let newname = null;

            for (var i = 0; i < this.userlist.length; i++) {
                    if (updateUser.id === this.userlist[i].id){
                            oldname = this.userlist[i].name
                            newname = updateUser.name
                            this.userlist[i] = updateUser
                    }
            }

            this.$buefy.toast.open({
                         message : `${oldname} changed to ${newname}`,
                         type: 'is-success',
                     })

        },
       deleteUser(id){
           this.userlist = this.userlist.filter(userlist => userlist.id != id);
       }
    }       
}

</script>


<style scoped>
.mt-r{
    margin-top: 1.25em;
}

h1{
    float: left;
}
</style>