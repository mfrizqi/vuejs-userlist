<template>
  <div>
      <section>
        <b-field label="Name">
            <b-input v-model="name" placeholder="Kevin Garvey"></b-input>
        </b-field>

        <b-field label="Username">
            <b-input v-model="username" placeholder="kevgar10" maxlength="30"></b-input>
        </b-field>

        <b-field label="Email">
            <b-input type="email"
                v-model="email"
                placeholder="kevingarvey@mail.com"
                maxlength="30">
            </b-input>
        </b-field>

        <b-field label="Division">
            <b-select placeholder="Select a subject" v-model="division">
                <option value="Front-End Developer">Front-End Developer</option>
                <option value="Back-End Developer">Back-End Developer</option>
                <option value="Project Manager">Project Manager</option>
                <option value="UI/UX Designer">UI/UX Designer</option>
            </b-select>
        </b-field>

        <b-field>
            <b-button @click="createUser"> Submit </b-button>
        </b-field>
    </section>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';


export default {
    name: 'UserForm',
    methods : {
        pressed(){
            this.$buefy.notification.open('Submitted!');
        },

        createUser(){
            const newUser = {
                id : uuidv4(),
                name : this.name,
                username : this.username,
                email : this.email,
                division: this.division
            }

            this.$emit('new-user', newUser);
        }
    }
}
</script>

<style>

</style>