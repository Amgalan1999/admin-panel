<template>
    <v-layout fluid>
      <v-container>
        <v-row>
          <v-col cols="12">
            <v-row
              :align="alignment"
              :justify="justify"
              style="height: 300px;"
            >
              <v-flex xs4>
                <v-card flat light class="ma-4 pa-6" color="white">
                  <v-card-title>
                    Quote Section
                  </v-card-title>
                  <v-card-text>
                    <v-textarea
                      label="Please Write The Quote Down Below"
                      outlined
                      light
                    ></v-textarea>
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs4>
                <v-card flat light class="ma-4 pa-6" color="white">
                  <v-card-title>
                    Author Section
                  </v-card-title>
                  <v-card-text>
                    <v-radio-group v-model="radio">
                      <v-radio
                        light
                        v-for="n in type"
                        :key="n"
                        :label="n"
                        :value="n"
                      ></v-radio>
                    </v-radio-group>
                    <v-flex v-if="radio == 'Book Quote'">
                      <v-text-field
                        label="Book"
                        v-model="author.book"
                        outlined
                      ></v-text-field>
                      <v-text-field
                        label="Author Name"
                        v-model="author.author"
                        outlined
                      ></v-text-field>
                    </v-flex>
                    <v-flex v-if="radio == 'Quote'">
                      <v-text-field
                        label="Author Name"
                        v-model="author.author"
                        outlined
                      ></v-text-field>
                    </v-flex>
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs4>
                <v-card flat light class="ma-4 pa-6" color="white">
                  <v-card-title>
                    Hashtag Section
                  </v-card-title>
                  <v-card-text>
                    <v-combobox
                      v-model="select"
                      :items="items"
                      small-chips
                      hide-selected
                      outlined
                      label="Select Hashtags of The Quote"
                      multiple
                    ></v-combobox>
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12>
                <v-btn block color="primary">Submit</v-btn>
              </v-flex>
            </v-row>
          </v-col>
        </v-row>
      </v-container>
    </v-layout>
</template>

<script>
  export default {
    data(){
      return{
        type: ["Book Quote", "Quote"],
        radio: null,
        author: null,
        quote: "",
        hashtag: [],
        items: ['some tags', 'another tags']
      }
    },
    watch: {
      radio: function(val){
        if(val == "Book Quotes") this.author = {book: "", author: ""};
        else this.author = {author: "" }
      }
    }
  }
</script>

<style scoped>

</style>
