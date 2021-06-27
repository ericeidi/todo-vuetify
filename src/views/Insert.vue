<template>
      <v-container
      >
        <v-row align="center"
            justify="center"
            >

            <v-text-field label="Insira a tarefa" 
            v-model="title"
            style="max-width: 500px"
            >
            </v-text-field>

            <div class="my-2 " style="margin-left: 5px">
            
              <v-btn 
              depressed small 
              color="primary" 
              @click="storeTask()">
              
              Adicionar</v-btn>
            </div>
        </v-row>
        <v-row align="center"
            justify="center"
           
            >
            <List 
            
            :taskList="taskList" 
            />  
        </v-row>
     </v-container>
</template>

<script>


import List from '../components/List';

  export default {
  name: 'Insert',

    components: {
      List
    },

    data: () => ({
      title: "",
      isCompleted: false,
      taskList: [],
    }),

    methods:  {
        storeTask(){
          this.taskList.push({
          newTask:this.title,  
          isCompleted:this.isCompleted
          })
          this.title = "";
        },
    }
  }
</script>
