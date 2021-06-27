<template>
<v-dialog v-model="show" max-width="500px">
  <v-card>
    <v-card-actions>
      <v-text-field
        v-model="title"
        required
      ></v-text-field>
      <v-btn 
        color="primary" 
        style="margin-left:10px" 
        text
        @click="changeTitle()"
        >Atualizar
      </v-btn>
      
    </v-card-actions>
  </v-card>
</v-dialog>
</template>

<script>
export default {

    

  props: {
    value: Boolean,
    title: String,
    taskList: []
  },

    
  computed: {
    show: {
      get () {
        return this.value
      },
      set (value) {
         this.$emit('input', value)
      }
    }
  },


  methods:{
      changeTitle() {
          this.taskList.newTask = this.title
          this.show = false;
          setTimeout(() => this.success = false, 2000);
      }
  },

}
</script>