<template>
  <div>
    <v-list-item 
    :class="{'green lighten-4 ': this.tarefa.concluido}"
    @click="doneTask()"
    >
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox :input-value="tarefa.concluido"></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title
              :class="{'text-decoration-line-through' : tarefa.concluido}"
              >{{tarefa.titulo}}</v-list-item-title>
            </v-list-item-content>

            <v-list-item-action>
              <v-btn 
              @click.stop="handleRemoveTarefa(tarefa.id)"
              icon>
                <v-icon color="red darken-1">mdi-trash-can</v-icon>
              </v-btn>
            </v-list-item-action>
          </template>
        </v-list-item>
        <v-divider></v-divider>
  </div>
</template>

<script>
export default {
 
  props:['tarefa'],
 
  methods:{
    doneTask(){
      let task = this.tarefa
      task.concluido = !task.concluido
    },

    handleRemoveTarefa(id){
      this.$store.commit('removeTarefa', id)
    }
  }
}


</script>

<style>

</style>