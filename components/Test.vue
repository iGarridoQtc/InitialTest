<template>
  <div>
    <!-- Ejemplo simple de componentes y reactividad -->
    <p>{{ hi }}</p>
    <p>{{ msg }}</p>
    <v-btn 
      outlined 
      color="blue" 
      :loading="loadingMsg"
      @click="onGetNewMsg"
    >
      New Msg
    </v-btn>

    <v-divider></v-divider>

    <!--
      Test:
      Crear una tabla simple y consumir una API pública para llenarla de datos, una fila a la vez. La idea es implementar todas las 
      funcionalidades que creas que mejoran su uso y experiencia.

      - Crear v-simple-table (vuetify v2 https://v2.vuetifyjs.com/en/components/simple-tables/) de 2 columnas, Quote y Author. 
      - Crear un v-btn que agregue una fila a la tabla cada vez que se presiona.
      - La lista debe quedar guardada en el store usando Vuex.
      - Implementar el borrado de elementos de la tabla (y del store).
      - Extra1: Implementar el ingreso manual de nuevas frases y autores a la lista.
      - Extra2: Implementar la edición de los elementos de la tabla.
    -->

  </div>
</template>

<script>
import { mapGetters } from 'vuex'

import {
  GET_NEW_MSG
} from '~/store/actions.types'

export default {
  data () {
    return {
      msg: 'hola!',
      loadingMsg: false,
      quotes: [
        { text: 'This is my first Quote', author: 'Ismael' }
      ]
    }
  },

  methods: {
    async onGetNewMsg () {
      try {
        this.loadingMsg = true
        const { quote } = await this.$store.dispatch(GET_NEW_MSG)
        this.msg = quote
      } catch (error) {
        console.log(error)
      } finally {
        this.loadingMsg = false
      }
    }
  },

  computed: {
    ...mapGetters([
      'hi'
    ])
  }
}
</script>

<style lang="scss" scoped>

</style>