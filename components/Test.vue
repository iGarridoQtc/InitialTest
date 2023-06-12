<template>
  <div>
    <p>{{ msg }}</p>
    <v-btn outlined color="blue" @click="onGetNewMsg">
      New Msg
    </v-btn>

    <v-divider></v-divider>

    <!-- Implementar una v-simple-table (de vuetify v2)-->

  </div>
</template>

<script>
  import {
    GET_NEW_MSG
  } from '~/store/actions.types'
  
  export default {
    data () {
      return {
        msg: 'hola!',
        quotes: [
          { text: 'This is my first Quote', author: 'Ismael' }
        ]
      }
    },

    methods: {
      async onGetNewMsg () {
        const { quote } = await this.$store.dispatch(GET_NEW_MSG)
        this.msg = quote
      }
    },
  }
</script>

<style lang="scss" scoped>

</style>