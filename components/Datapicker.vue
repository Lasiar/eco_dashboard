<template>
    <v-form ref="form" v-model="valid" lazy-validation>
        <v-menu
                ref="start"
                :close-on-content-click="false"
                v-model="start"
                :nudge-right="40"
                :return-value.sync="date_start"

                transition="scale-transition"
                offset-y
                full-width
                min-width="290px"
        >
            <v-text-field
                    slot="activator"
                    v-model="date_start"
                    :label="atr"
                    prepend-icon="event"
                    readonly
                    required
            ></v-text-field>
            <v-date-picker
                    locale="ru-Latn"
                    v-model="date_start"
                    @input="$refs.start.save(date_start)"
                    :first-day-of-week="1"
            ></v-date-picker>
        </v-menu>
        <v-menu
                ref="finish"
                :close-on-content-click="false"
                v-model="finish"
                :nudge-right="40"
                :return-value.sync="date_finish"

                transition="scale-transition"
                offset-y
                full-width
                min-width="290px"
        >
            <v-text-field
                    slot="activator"
                    v-model="date_finish"
                    :label="atr"
                    prepend-icon="event"
                    readonly
                    required
            ></v-text-field>
            <v-date-picker
                    locale="ru-Latn"
                    v-model="date_finish"
                    @input="$refs.finish.save(date_finish)"
                    :first-day-of-week="1"
            ></v-date-picker>
        </v-menu>
        <v-btn
                :disabled="!valid"
                @click="submit"
        >
            submit
        </v-btn>
    </v-form>
</template>

<script>
    export default {
      name: 'Datapicker',
      props: ['atr'],
      data: function () {
        return {
          finish: false,
          start: false
        }
      }
    }
</script>

<style scoped>

</style>