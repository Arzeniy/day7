<template>
    <div>
        <input v-model="Login">
        <button @click="auth()">Ok</button>
    </div>
</template>
<script>
    import Vue from 'vue'
    import axios from 'axios'
    import VueAxios from 'vue-axios'

    Vue.use(VueAxios, axios)

    export default {
        data: function() {
            return {
                Login:""
            };
        },
        methods: {
            auth () {
                Vue.axios.get("http://46.101.212.195:3000/students/name/"+this.Login).then((response) => {
                    if (response.data === null ) {
                        return
                    }
                    console.log('response', response.data)
                    this.$store.commit('setUser', response.data);
                    this.$router.push('/');
                })
            }
            }
    }
    </script>