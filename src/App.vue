<!--helloVue/src/App.vue-->
<template>
  <div>
    
    <table>
      <tbody>
    
          
        <p>BITCOIN</p>

        <li v-for="(value,key) in todos">
          {{ key }}:{{ value.description }}
        </li>
        <li v-for="(value,key) in bpiEUR">
          {{ key }}:{{ value }}
        </li>
         
       
        
      </tbody>
    </table>

  </div>
</template>

<script>

import axios from 'axios' 

export default {
  data() {
    return { 
      todos: null,
      bpiEUR: null,
      bpiUSD: null
    };
  },
  mounted(){
    console.log('Hola mounted')
    this.getTodos();
    
  },
  methods: {
    getTodos(){
      axios
      .get('https://api.coindesk.com/v1/bpi/currentprice.json')
      .then(response => {
        console.log(response.data  )
        this.todos = response.data.bpi
        this.bpiEUR = response.data.bpi.EUR
        this.bpiUSD = response.data.bpi.USD

        })
    }
  }
};
</script>
