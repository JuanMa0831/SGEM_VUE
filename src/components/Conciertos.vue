<template>
    <div>
      <h1>Conciertos</h1>
      <ul>
        <li v-for="concierto in conciertos" :key="concierto.id">
          {{ concierto.nombre }} - {{ concierto.fecha }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        conciertos: []
      };
    },
    mounted() {
      this.fetchConciertos();
    },
    methods: {
      fetchConciertos() {
        axios.get('http://localhost:8000/api/conciertos')
          .then(response => {
            this.conciertos = response.data;
          })
          .catch(error => {
            console.error(error);
          });
      }
    }
  };
  </script>