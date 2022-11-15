<template>
  <v-container>
    <v-row>
      <v-col
          v-for="book in books"
          :key="book.title"
          cols="4"
      >
        <v-card height="200">
          {{ book.title }}
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  //import HelloWorld from '../components/HelloWorld'

  export default {
    name: 'Home',

    data(){
      return{
        test: 'Testna varijabla',
        books: []
      }
    },
    created() {
      this.getData();
    },
    methods: {
      getData(){
        let api = "https://api.nytimes.com/svc/books/v3/lists/best-sellers/history.json"
        this.axios.get(api,  {
          params: {
            'api-key':  '663gxgca9HwVo1apZbmu3iYD6Gi6Sh6G'
          }
        }).then((response)=>{
          console.log(response.data)
          this.books = response.data.results
        })
      }
    }
    //components: {
      //HelloWorld,
    //},


  }
</script>
