
<template>
  <!--<div>
      <h1>Do to list</h1>
      <form @submit.prevent="addItem" autocomplete="off">
        <AddTask/>
        <button class="button btn-add">Add</button>

        
      </form>
      <ul>
          <li> <button v-on:click= "deleteItem(index)"></button></li>

      </ul>
      


  </div>-->

  <div class="wrapper">

    <div class="addlist">
      <h1>Simple to-do list</h1>
     <!--<label> Your tasks: {{ isComplete }} / {{ totalItems }}</label>-->
     <!--to add new item into the list -->
    
     <AddTask @add="(item) => items.push(item)" ></AddTask>
     
     <!--Show added items in list view-->
     <ul class="task-list">
       <!--  v-for to iterates over the items array and create a list of item for each item in the array -->
       <!--   v-bind to check whether item is completed or not-->
       <li class="task-list-item" v-for="(item, index) in items" :key="index" >
        <!-- <input type="checkbox" 
          v-model="items.completed"/>-->
          
          <span v-if="(item.EditMode== false)">{{ item.text }}</span>
          <input v-if="(item.EditMode == true)"
          type="text"
          class="task-input"
          v-model="editItem"
          placeholder="Get groceries"/>

          <select v-if="!showSelectedOption" v-model="selectedOption" @change="hideDropdown" name="prioritaire" id="prioritaire" >
            <option value="">Quel priorité?</option>
            <option value="Urgent">Trés prioritaire</option>
            <option value="Prioritaire" class="Prioritaire">moyen prioritaire</option>
            <option value="Optionnel" class="Optionnel">pas prioritaire</option>
          </select>
          <div  v-for="( index) in items" :key="index">
          <span class="prioriter" v-if="showSelectedOption"> {{ selectedOption }}</span>
          </div>
          <button v-on:click="saveItem(index, editItem)" v-if="(item.EditMode == true)" >Save</button>
          <!--  delete item on click-->
          

          <DeleteTask @delete="(i) => items.splice(i,1)" v-bind:titi="index" ></DeleteTask>
         <!-- Bonton edit-->
          <EditTask @EditTask="(e) => items[e].EditMode= !items[e].EditMode" v-bind:titi="index"  />
            </li>
          </ul>
        </div>
        
    <!--</form>-->
  </div>
</template>

<script>

import AddTask from "./components/AddTask.vue";
import DeleteTask from "./components/Delete.vue";
import EditTask from "./components/Remove.vue";
export default {
  name :'App',
  components : {
    AddTask,
    DeleteTask,
    EditTask
  },
  data() {
    return{
    items: [],
    editItem: "",
    selectedOption: "",
    showSelectedOption: false,
  }
  },
 computed: {
    /*totalItems() {
      return this.items.length; //auto increment of 1 of each items added into array
    },
    isComplete() {
      return this.items.filter(item => item.completed).length; //to get completed [checkbox: checked] 
    }*/
  },
  methods: {

    saveItem(index, editItem){
     
     
      this.items[index].text= editItem
      this.items[index].EditMode = false
      this.editItem=""
    },

    hideDropdown() {
      this.showSelectedOption = true;
    },
    /*addItem() {
      if (this.newItem !== "") {
        this.items.push({text: this.newItem, completed: false}); //check if input field is empty, if not empty then push [input] into array [items] and mark not completed [checkbox: unchecked]
        this.newItem = ""; //input becomes empty
      }
    },
    deleteItem(index) {
      this.items.splice(index, 1); //remove item
    }*/

  },
};
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  
  color: #2c3e50;
  margin-top: 60px;
}
.wrapper{


  background-image:url(assets/fond_liste.jpga);
  background-size: cover;
  
  width: 1000px;
  height: 900px;

  text-align: center;
}
.addlist{
  position: relative;
  top: 50%
}
li{
  list-style:none ;
  
  margin-bottom: 1%;
  margin-left: 30%;
  margin-right: 30%;
}
.prioriter{
  margin-left: 3px;
}

.Urgent{
  color: red;
}
</style>
