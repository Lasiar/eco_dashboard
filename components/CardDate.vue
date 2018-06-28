<template>
    <div>
        <v-card dark color="secondary">
            <v-card-title primary-title>
                {{name}}
            </v-card-title>
            <v-card-actions>
                <DataPicker @change="getStartDate" atr="Начало"/>
                <DataPicker @change="getFinishDate" atr="Конец"/>
                <v-btn
                        :disabled="!valid">
                    test
                </v-btn>
            </v-card-actions>
        </v-card>
    </div>
</template>

<script>
    import DataPicker from '../components/Datapicker'

    export default {
      components: {DataPicker},
      name: 'CardDate',
      props: ['name'],
      data: function () {
        return {
          date_start: '',
          date_finish: '',
          message: ''
        }
      },
      methods: {
        getStartDate: function (data) {
          this.date_start = data
        },
        getFinishDate: function (data) {
          this.date_finish = data
        }
      },
      computed: {
        valid: function () {
          let self = this
          if (this.date_start === '') {
            self.message = ''
            return false
          }
          if (this.date_finish === '') {
            self.message = ''
            return true
          }
          if (this.date_start > this.date_finish) {
            self.message = 'Первая дата не может быть больше второй!'
            return false
          } else {
            self.message = ''
            return true
          }
        }

      }
    }
</script>

<style scoped>

</style>