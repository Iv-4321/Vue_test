<template>

    <v-app>
        <v-col lg>
            <v-card>
                <v-card-title>
                    Book Catalog
                </v-card-title>
                <v-row>
                    <v-col>
                        <v-select v-model="book"
                                  :items="books"
                                  item-text="name"
                                  item-value="genre"
                                  label="Book name"
                                  prepend-icon="mdi-book-search"
                                  filled>
                        </v-select>
                    </v-col>
                </v-row>
                <v-divider></v-divider>
                <v-card-text>
                    <v-list-item v-for="book in books" :key="book.id" :to="book.pdf">
                        <v-list-item-avatar>
                            <img :src="book.picture" fluid />
                        </v-list-item-avatar>
                        <v-list-item-content>
                            <v-list-item-title>
                                <h5 class="text-h5">{{book.name}}</h5>
                            </v-list-item-title>
                            <v-list-item-subtitle>
                                <b>{{book.author}}</b>
                            </v-list-item-subtitle>
                        </v-list-item-content>
                        <v-list-item-action>
                            <v-btn icon>
                                <!--<button v-on:click="openPdf" id='button' cssClass='e-small'>Read </button>-->

                                <v-icon>mdi-book-open-blank-variant</v-icon>
                            </v-btn>
                        </v-list-item-action>
                    </v-list-item>
                </v-card-text>
            </v-card>
        </v-col>
    </v-app>

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
            openPdf() {
                alert('You clicked!')
            }
        }
}
</script>