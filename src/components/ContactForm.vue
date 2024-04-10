<script>
import axios from 'axios'

import {store} from '../store.js'

export default {
    name: 'ContactForm',
    components: {

    },
    data() {
        return {
            store,
            name:'',
            email:'',
            message:''
        }
    },
    methods() {
        sendForm(){
            const data = {
                name: this.name,
                email: this.email,
                message: this.message
            }

            this.errors = {};

            axios.post(`${this.store.apiBaseUrl}/api/contacts`, data)
            .then(res => {

                this.success = res.data.success

                if(!this.success) {
                    this.errors = res.data.errors
                } else {
                    this.name = ''
                    this.email = ''
                    this.message= ''
                }
            })
        }

    },
    mounted() {

    }
}
</script>

<template>
    <div>
        <h1 class="text-center mt-4">Contattami:</h1>

        <div class="alert alert-success" v-if="success" role="alert">
            Messaggio inviato correttamente
        </div>
    </div>

    <div>
        <form @submit.prevent="sendForm()">
            <div>
                <input type="text" class="form-control">
            </div>
        
        </form>
    </div>
</template>

<style>

</style>