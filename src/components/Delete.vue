<template>
  
  
  
  <!-- Add item on click -->
  
  <button @click="$emit('delete',deleteItem())"  class="button btn-add"><i class="fa-solid fa-trash"></i></button>
  
  
</template>

<script>
  export default {

    name: 'DeleteTask',
   /* props : ["titi"],*/
    props : ["titi"],
    
    methods : {
        deleteItem() 
        {
          console.log(this.titi)
          
            return this.titi
          //this.items.splice(index, 1); //remove item
        }
    },
      
    
  
 }
    //}
  
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
    button{
      margin-left: 2%;
    }
  </style>
  