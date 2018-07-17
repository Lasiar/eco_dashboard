<template>
    <v-container grid-list-md text-xs-center>
        <v-layout row wrap>
            <v-flex xs6>
                <CardDate :save-date=message[0] name="all"></CardDate>
            </v-flex>
            <v-flex xs6>
                <card-date :save-date=message[1] name="pb"></card-date>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
 import axios from 'axios'
 import DataPicker from '../components/Datapicker'
 import CardDate from '../components/CardDate'

 export default {
   components: {CardDate, DataPicker},
   data () {
     return {
       message: [{
         who: String,
         date_start: String,
         date_finish: String
       }, {
         who: String,
         date_start: String,
         date_finish: String
       }],
       error: ''

     }
   },
   mounted: function () {
     let self = this
     self.isLoading = false
     axios.post('http://127.0.0.1:8080/get-date')
       .then(function (response) {
         self.message = response.data
         console.log(response.data)
       })
       .catch(function (error) {
         self.error = error.message
       })
       .finally(function () {
         self.isLoading = true
       })
     self.showModal = true
   }
 }
</script>