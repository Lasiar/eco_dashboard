<template>
    <v-container grid-list-md text-xs-center>
        <v-layout row wrap>
            <v-flex xs6>
                <CardDate name="Все"></CardDate>
            </v-flex>
            <v-flex xs6>
                <card-date name="Свинец"></card-date>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
    import DataPicker from '../components/Datapicker'
    import CardDate from '../components/CardDate'

    export default {
      components: {CardDate, DataPicker},
      data () {
        return {
          menu2: false
        }
      }
    }
</script>
g