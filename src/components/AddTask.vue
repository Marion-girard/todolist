<template>
    <div class="task">
      
      <input
        type="text"
        class="task-input"
        v-model="newItem"
        placeholder="Get groceries"
      />
        <!-- Add item on click -->
       <button @click="$emit('add',addItem())"  class="button btn-add">Add</button>
      
      
    </div>
  </template>
  
  <script>
  export default {
    name: 'AddTask',
   
    data(){

      return{
         
          newItem:""
      }
        
    },
   
    methods : {
      addItem() {
       
        
        //this.newItem.push({text: this.newItem, completed: false}); //check if input field is empty, if not empty then push [input] into array [items] and mark not completed [checkbox: unchecked]
        const item=
        {
          text: this.newItem,
          EditMode: false
        };
        console.log(item)
        
        //if (this.newItem !== ""){
          
          this.newItem ="" //input becomes empty
          return item
        
      }
    },
  
      }
    //}
  
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
 
  </style>
  