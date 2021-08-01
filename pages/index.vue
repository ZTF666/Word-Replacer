<template>
   <div>
    <v-form @submit.prevent="ProcessText()">
      <v-container class="up">
        <v-layout row wrap class="d-flex justify-center">
          <v-flex xs12 sm12 md12>
            <v-row>
              <v-col cols="12" sm="12" md="12">
                <v-textarea
                 outlined
                  auto-grow
                  label="You Text Goes Here"
                  v-model="Input"
                ></v-textarea>
              </v-col>
            </v-row>

            <v-row class="d-flex justify-center">
              <div>
                <v-text-field
                  label="Word To Replace"
                  outline
                  v-model="WtC"
                  aria-autocomplete="false"
                ></v-text-field>
              </div>
            </v-row>
            <v-row class="d-flex justify-center">
              <div>
                 <v-text-field
                  label="Replace By"
                  outline
                  v-model="RbW"
                  aria-autocomplete="false"
                ></v-text-field>
              </div>
            </v-row>
            <v-row class="d-flex justify-center">
              <div>
                <v-col>
                  <v-btn color="secondary" @click.prevent="ProcessText()" class="primary--text">♻️Process♻️</v-btn>
                  <v-btn color="pinkish" @click.prevent="ClearText()" class="primary--text">🗑️Clear🗑️</v-btn>
                </v-col>
              </div>
            </v-row>

          </v-flex>
        </v-layout>
      </v-container>
    </v-form>
    <!-- OUTPUT -->

    <v-container class="up">
        <v-layout row wrap class="d-flex justify-center">
          <v-flex xs12 sm12 md12>
            <v-row>
              <v-col cols="12" sm="12" md="12">
                <v-textarea
                readonly
                 outlined
                  auto-grow
                  label="Output"
                  v-model="Output"
                  id="output"
                ></v-textarea>
              </v-col>
            </v-row>
             <v-row class="d-flex justify-center">
              <div>
                <v-col>
                  <v-btn color="secondary" @click.prevent="CopyToClip()" class="primary--text"><v-icon>mdi-clipboard-text</v-icon></v-btn>
                </v-col>
              </div>
            </v-row>
          </v-flex>
        </v-layout>
    </v-container>



   </div>
</template>

<script>
export default {
    head: {
    title: 'Word ♻️ Replacer',
    meta: [
      {
        hid: 'Word Replacer landing page',
        name: 'Word ♻️ Replacer page',
        content: 'Generate a QR code for your links and texts and download it in no time !!',
      },
    ],
  },
  data(){
    return{
      WtC:'',
      RbW:'',
      Input:'',
      Output:'',

    }
  },
  methods:{
    ProcessText(){
      if(this.Input !=null && this.WtC !=null && this.RbW !=null){
          let str = this.Input
          // Basically creating our own Regex depending on the user's input 
          let wordToChange = new RegExp(this.WtC, "gi");
          let ReplaceByWord = this.RbW
          let res = str.replace(wordToChange,ReplaceByWord)
          this.Output = res
          return
      }
     
    },
    CopyToClip(){
      if(this.Output !=null){
      var copyText = document.getElementById("output");
      copyText.select();
      copyText.setSelectionRange(0, 99999);
      document.execCommand("copy");
      }

    },
    ClearText(){
      this.Input=''
      this.Output=''
      this.WtC=''
      this.RbW=''
    }
  },
  created(){
    console.log('Iam looking for a job , contact me if you can offer me one , thank you 😊 ')
  }

}
</script>

<style scoped>
.up{
  margin-top: 50px;
}

</style>