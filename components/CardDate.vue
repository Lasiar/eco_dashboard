<template>
    <v-card dark color="secondary">
        <v-card-title primary-title>
            Название
        </v-card-title>
        <v-card-actions>
            <Datapicker atr="Начало"/>
            <Datapicker atr="Конец"/>
        </v-card-actions>
    </v-card>
</template>

<script>
    export default {
      name: 'CardDate'
    }
</script>

<style scoped>

</style>