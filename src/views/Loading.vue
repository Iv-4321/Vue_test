<template>
    <v-container>
      <div class="container">
        <div class="large-12 medium-12 small-12 cell">
          <label>File
            <v-file-input type="file" id="file" ref="file"  v-model="file" />
          </label>

            <div class="large-12 medium-12 small-12 cell">
            <button v-on:click="addFile()">Add File</button>
            </div>
        </div>
      </div>
    </v-container>

</template>

<script>
import axios from 'axios'

  export default {
    data(){
      return {
        file: null,
      }
    },
    methods: {

      addFile(){
        let formData = new FormData();
          formData.append('file', this.file);

        axios.post( 'http://127.0.0.1:8000/api/books/', formData)
            .then((response) => {
                        console.log(response);
                    })
                    .catch((error) => {
                        console.log(error);
                    });
      }
    }
  }
</script>