<template>
  <div id="app">
    <div id="nav">

        <v-bottom-navigation>
            <router-link to="/"
                         tag="v-btn">
                <v-btn>
                    <span>Home</span>
                    <v-icon>mdi-home-circle-outline</v-icon>
                </v-btn>
            </router-link>
            <router-link to="/auth"
                         tag="v-btn">
                <v-btn>
                    <span>Sign In</span>
                    <v-icon>mdi-login</v-icon>
                </v-btn>
            </router-link>
            <router-link to="/Registr"
                         tag="v-btn">
                <v-btn>
                    <span>Registr</span>
                    <v-icon>mdi-account-plus-outline</v-icon>
                </v-btn>
            </router-link>
            <router-link to="/Search"
                         tag="v-btn">
                <v-btn>
                    <span>Search</span>
                    <v-icon>mdi-layers-search-outline</v-icon>
                </v-btn>
            </router-link>
            <router-link to="/Loading"
                         tag="v-btn">
                <v-btn>
                    <span>Loading</span>
                    <v-icon>mdi-database-export-outline</v-icon>
                </v-btn>
            </router-link>

        </v-bottom-navigation>
    </div>
    <router-view/>
  </div>

</template>

<script>
    import axios from 'axios'



    export default {
        name: "Books",
        components: {
        },
        data:() => ({
            books: [],
        }),

        watch: {
        },
        created() {
            axios.get('http://127.0.0.1:8000/api/books/')
                .then(response => {
                    console.log(response);
                    this.books = response.data;
                    console.log(this.books);
                })
                .catch(error => {
                    console.log(error);
                })
                .then(function () {
                });
        },
        computed: {
        },
        methods: {
            getpdf(file) {
                window.open("" + file, "");
            }
        }
}
</script>

