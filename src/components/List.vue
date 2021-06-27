<template>
 <v-simple-table>
      
              <template v-slot:default>
                <thead>
                  <tr>
                    <th>Concluído</th>
                    <th class="text-left"  style="min-width:500px">
                      Tarefas
                    </th>
                    <th>
                        Ação
                    </th>
                  
                  </tr>
                </thead>
                <tbody>
                  <tr
                    v-for="(item, index) in taskList"
                    v-bind:key="index"
                  >

                    <td>
                        <v-checkbox
                        v-model="checkbox"
                        v-on:change="handleCompletedCheckbox(index)"
                        ></v-checkbox>
                    </td>

                    <td>{{ item.newTask }}</td>
                  
                    <td>
                    <v-btn
                        style="margin-right: 10px"
                        
                        @click="showUpdateList=true"
                     >
                       <v-icon>{{ icons.mdiPencil }}</v-icon>
                    </v-btn>

                    <UpdateModal 
                    v-model="showUpdateList" 
                    :title="item.newTask" 
                    :taskList="taskList[index]"
                    
                    />

                     <v-btn color="error"
                        @click="deleteRow(index)"
                     >

                        <v-icon >
                            {{ icons.mdiDelete }}
                        </v-icon>

                    </v-btn>
                    </td>
                  </tr>
                <SuccessAlert
                :success="success"
                :descricao="descricao.deletar"
                />
                </tbody>
              </template>
        </v-simple-table>
</template>        
<script>
 
 import {
    mdiDelete,
    mdiPencil
    } from '@mdi/js'

import UpdateModal from './UpdateModal'
import SuccessAlert from './SuccessAlert'

export default {

    
    name: 'List',

    data: () => ({
      icons: {
        mdiDelete,
        mdiPencil
      },

      showUpdateList: false,
      success: false,

      descricao: {
        deletar: "deletado",
      },

      checkbox: false

    }),

    components: {
      UpdateModal,
      SuccessAlert
    },

    


    props: {
        taskList: []
    },

    methods: {
    deleteRow (index) {
      this.$delete(this.taskList, index)
      this.success = true;
      setTimeout(() => this.success = false, 2000);

    },

    handleCompletedCheckbox(index){
       this.taskList[index].isCompleted == false ? this.taskList[index].isCompleted = true : this.taskList[index].isCompleted = false;
    }

  }
}
</script>