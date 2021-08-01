<template>

   <v-container class="up">
        <v-layout row wrap class="d-flex justify-center">
          <v-flex xs8 sm12 md12>
            <v-row>
              <v-col cols="12" sm="12" md="12">
                <v-img src="https://media.giphy.com/media/5nmobhwPiNsKELWk69/giphy.gif"></v-img>
                <center><h1 class="secondary--text">By the gods !!! what have you done ? </h1>
                <v-btn nuxt link to='/' color="secondary" class="primary--text">Go Back</v-btn></center>
              </v-col>
            </v-row>
          </v-flex>
        </v-layout>
   </v-container>

</template>

<script>
export default {
  layout: 'empty',
  props: {
    error: {
      type: Object,
      default: null
    }
  },
  data () {
    return {
      pageNotFound: '404 Not Found',
      otherError: 'An error occurred'
    }
  },
  head () {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError
    return {
      title
    }
  }
}
</script>

<style scoped>
h1 {
  font-size: 20px;
}
</style>
