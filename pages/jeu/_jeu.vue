<template>
    <div class="content">
        <h1>{{jeux.post_title}}</h1>

        <p>{{jeux.post_content}}</p>

        <!-- .replace(/<(.+?)>/g, ' ').replace(/ {2,}/g, ' ') Regex ne fonctionne pas-->
    </div>
    
</template>

<script>
import axios from 'axios';

export default {
    data() {
        return{
            jeux: []
        }
    },
    mounted() {
        let nbr = this.$route.params.jeu;
        console.log(this.$route.params);
        axios.get('http://sitetest.local/wp-json/wp/v2/jeux_video').then(response => {
            this.jeux = response.data[nbr];console.log(this.jeux)
            });
        console.log(nbr);
    }
}
</script>

<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>

<style>

    h1{
        padding-top: 2rem;
        display: flex;
        justify-content: center;
    }

</style>
