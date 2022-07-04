<template>
    <div>
        <div class="header">
            <h1>{{ msg }}</h1>

            <div class="searchInDevs">
                <label for="searchDev">Search your Dev</label>
                <input type="searchDev" name="search" id="searchDev">
                <button type="submit">Search</button>
    <!--        v:model-->
            </div>
        </div>

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

                <input class="devButton" type="button"  :value="'See ' + currency.name.first + ' ' + currency.name.last">
<!--                @click="displayCard"-->
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
/*<!--*, ::before, ::after {-->*/
/*<!--    box-sizing: border-box;-->*/
/*<!--    margin: 0;-->*/
/*<!--    padding: 0;-->*/
/*<!--}-->*/

body {
    font-family: Arial, Helvetica, sans-serif;
}

.header {
    margin: 0;
    height: 200px;
    padding: 60px;
    background-color: darkblue;
}

h1 {
    color: aliceblue;
    margin-bottom: 60px;
}

h2 {
    color: darkblue;
}

.name, .email {
    margin: 20px;
}

.devButton {
    margin-top:20px;
    padding: 10px;
    background-color: darkblue;
    border: none;
    border-radius: 6px;
    color: aliceblue;
}

.devList {
    margin: 0 200px;
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

.searchInDevs {
    max-width: 700px;
    width: 70%;
    margin: 30px auto;
    position: relative;
    display: flex;
}

#searchDev {
    width: 100%;
    padding: 15px;
    border: none;
    outline: none;
    border-radius: 3px;
}

.searchInDevs label {
    position: absolute;
    color: darkblue;
    top: 50%;
    transform: translateY(-50%);
    padding-left: 8px;
    transition: all 0.3s ease-in;
}

.searchInDevs button {
    margin-left: 5px;
    padding: 15px;
    background-color: aliceblue;
    color: darkblue;
    border: none;
    border-radius: 3px;
}

.searchInDevs:focus-within label {
    top: -15px;
    padding-left: 5px;
    color: aliceblue;
}

</style>