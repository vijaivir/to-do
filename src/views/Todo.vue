<template>
  <div class="home">
    <v-list
      subheader
      flat
    >
      <v-subheader>Todo</v-subheader>
      <v-divider></v-divider>
      <div
        v-for="task in tasks"
        :key="task.id"
      >
        <v-list-item
          @click="doneTask(task.id)"
          :class="{'blue lighten-5': task.done}"
        >
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox
                :input-value="task.done"
                color="primary"
              ></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title
                :class="{'text-decoration-line-through': task.done}"
              >
                {{task.title}}
              </v-list-item-title>
            </v-list-item-content>
          <v-list-item-action>
          <v-btn icon>
            <v-icon color="grey lighten-1">mdi-delete</v-icon>
          </v-btn>
          </v-list-item-action>
          </template>
        </v-list-item>
        <v-divider></v-divider>
      </div>
    </v-list>
  </div>
</template>

<script>
  export default {
    name: 'Home',
    data(){
      return {
        tasks: [
          {
            id: 1,
            title: 'Add Tasks',
            done: false
          },
          {
            id: 2,
            title: 'Add Task 1', 
            done: false
          },
          {
            id: 3,
            title: 'Add Task 2', 
            done: false
          }
        ]
      }
    },
    methods: {
      doneTask(id){
        let task = this.tasks.filter(task => task.id === id)[0]
        task.done = !task.done
      }
    }
  }
</script>
