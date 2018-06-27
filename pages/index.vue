<template>
    <v-container grid-list-md text-xs-center>
        <v-layout row wrap>
            <v-flex xs6>
                <v-card dark color="secondary">
                    <v-card-title primary-title>
                        Все
                    </v-card-title>
                    <v-card-actions>
                            <Datapicker atr="Начало"/>
                    </v-card-actions>
                </v-card>
            </v-flex>
            <v-flex xs6>
                <v-card dark color="secondary">
                    <v-card-title primary-title>
                        Свинец
                    </v-card-title>
                    <v-card-actions>
                        <Datapicker atr="Начало"/>
                    </v-card-actions>
                </v-card>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
    import Datapicker from '../components/Datapicker'

    export default {
      components: {Datapicker},
      data () {
        return {
          menu2: false
        }
      }
    }
</script>
g