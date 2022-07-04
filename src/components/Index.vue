<template>
    <div>
        <h1>{{ msg }}</h1>

        <div class="dev" v-for="currency in response" :key="currency.email">

            <img :src="currency.picture.medium" :alt="currency.name.last+' picture'">

            <div class="name">
            {{ currency.name.title }} {{ currency.name.first }} {{ currency.name.last }}
            </div>

            <div class="email">
                {{ currency.email }}
            </div>

            <div class="phone">
                {{ currency.phone }}
            </div>

        </div>

        <pre>
            {{ response }}
        </pre>
    </div>
</template>

<script>
import axios from "axios";

export default {
    name: 'Index',

    props: {
        msg: String
    },

    data () {
        return {
            response: null
        }
    },

    mounted() {
        document.title = "Developers Index";

        axios
            .get('https://randomuser.me/api/')
            .then(response => (this.response = response.data.results))
    }
}
</script>

<style>

</style>