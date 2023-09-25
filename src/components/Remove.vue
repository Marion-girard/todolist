<template>
   
      
      <!--<input
        type="text"
        class="task-input"
        v-model="newItem"
        placeholder="Get groceries"
      />-->
        <!-- Add item on click -->
        <button @click="$emit('EditTask',EditItem())"  class="button btn-edit"><i class="fa-solid fa-pen"></i></button>
      
    
  </template>
  
  <script>
  export default {
    name: 'EditTask',
    props : ["titi"],
    data(){
      return{
         

      }
        
    },
  
      
    methods : {
       EditItem() {
        
        console.log(this.titi)
          
        return this.titi
     
      },
      
    },
  
  }
    
  
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->

  <style scoped>

  </style>