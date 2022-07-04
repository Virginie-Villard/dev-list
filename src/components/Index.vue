<template>
    <div>
        <h1>{{ msg }}</h1>

        <div class="devList">

            <div class="devCard" v-for="currency in response" :key="currency.email">
                <img :src="currency.picture.medium" :alt="currency.name.last+' picture'">

                <h2 class="name">
                {{ currency.name.title }} {{ currency.name.first }} {{ currency.name.last }}
                </h2>

                <div class="email">
                    <strong>e-mail: </strong>{{ currency.email }}
                </div>

                <div class="phone">
                    <strong>Phone: </strong>{{ currency.phone }}
                </div>

                <input class="button" type="button" @click="displayCard" :value="'See ' + currency.name.last">
            </div>


        </div>

<!--        <pre>-->
<!--            {{ response }}-->
<!--        </pre>-->
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
            .get('https://randomuser.me/api/?results=12')
            .then(response => (this.response = response.data.results))
    }
}
</script>

<style>
body {
    margin: 0 200px;
}

h1, h2 {
    color: darkblue;
}

.name, .email {
    margin: 20px;
}

.devList {
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
}

.devCard {
    flex: 0 0 26%;
    margin: 20px auto;
    border-radius: 6px;
    box-shadow: 0 0 10px 5px rgba(0, 0, 0, 0.40);
    height: 300px; /* A changer ! */
    padding: 20px;
}

</style>