<template>
    <div>
        <v-card dark color="text-align: center; secondary">
            <v-card-title primary-title>
                <div>
                    <h3 class="headline mb-0">{{name}}</h3>
                    <div>{{existDateStart}} -  {{existDateFinish}} </div>
                </div>
            </v-card-title>
            <v-card-actions>
                <DataPicker :save-date=saveDate.date_start @change="getStartDate" atr="Начало"/>
                <DataPicker :save-date=saveDate.date_finish @change="getFinishDate" atr="Конец"/>
                <v-btn
                        @click.native="update"
                        :disabled="!valid">
                    test
                </v-btn>
            </v-card-actions>
        </v-card>
    </div>
</template>

<script>
    import DataPicker from '../components/Datapicker'
    import axios from 'axios'

    export default {
      components: {DataPicker},
      name: 'CardDate',
      props: {
        name: String,
        saveDate: {
          who: String,
          date_start: String,
          date_finish: String
        }
      },
      data: function () {
        return {
          date_start: '',
          date_finish: '',
          message: '',
          info: '',
          success: ''

        }
      },

      methods: {
        getStartDate: function (data) {
          this.date_start = data
        },
        getFinishDate: function (data) {
          this.date_finish = data
        },
        update: function () {
          let self = this
          self.isLoading = false
          console.log('i mam here')
          axios.post('/update', {who: this.name, date_start: this.date_start, date_finish: this.date_finish})
            .then(function (response) {
              if (response.data.success) {
                self.info = 'обновлено'
                self.success = true
              } else {
                console.log(response)
                self.info = 'не обновлено'
                self.success = false
              }
            })
            .catch(function (error) {
              self.info = 'Ошибка! Не могу связаться с API: ' + error
              self.success = false
            })
            .finally(function () {
              self.isLoading = true
            })
          self.showModal = true
        }
      },
      computed: {
        existDateStart: function () {
          console.log(this.saveDate)
          return this.saveDate.date_start
        },
        existDateFinish: function () {
          console.log(this.saveDate)
          return this.saveDate.date_finish
        },
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