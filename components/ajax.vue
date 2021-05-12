<template>
    <div id="ajax">
        <h1>Los personajes de SNK</h1>

        <section v-if="errored">
            <p>Lo sentimos, no es posible obtener la información en este momento.</p>
        </section>

        <section v-else>
            <div v-if="loading">
                cargando...
            </div>

            <div
            v-else
            v-for="currency in info"
            :key="currency"
            >
            <img v-bind:src="currency.img" v-bind:alt="currency.name"> 
            <p>{{currency.name}}</p>
            </div>

        </section>
    </div>    
</template>

<script>

import axios from 'axios';

export default {
    name: 'ajax',
    el: '#ajax',
    data () {
        return {
            info: null,
            loading: true,
            errored: false
        }
    },
    mounted () {
        axios
            .get('https://my-json-server.typicode.com/Joanutsu/SNK-JSON/SNK')
            .then(response => {
                this.info = response.data
            })
            .catch(error => {
                console.log(error)
                this.errored = true
            })
            .finally(() => this.loading = false)
    }
}

</script>

<style>

</style>