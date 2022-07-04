<template>
  <div class="container" style="max-width: 1000px">
    <div class="d-flex mt-3" >
      <input
        type="text"
        v-model="task" required
        placeholder="Geben Sie die Erinnerung bitte ein"
        class="w-200 form-control"
      />
      <button class="btn btn-warning rounded-1 " @click="submitTask">
        Hinzufügen
      </button>
      <form>
        <input class="btn btn-danger rounded-1" type="submit" value="Alle Erinnerungen löschen" @click='deleteTask'>
      </form>
    </div>

    <table class="table table-bordered mt-5" >
      <thead>
      <tr>
        <th scope="col">Erinnerung</th>
        <th scope="col" style="width: 150px">Status</th>
        <th scope="col" class="text-center">Löschen</th>
        <th scope="col" class="text-center">Bearbeiten</th>
        <th scope="col">Uhrzeit</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(task, index) in tasks" :key="index">
        <td>
            <span :class="{ 'line-through': task.status === 'Abgeschlosssen' }">
              {{ task.name }}
            </span>
        </td>
        <td>
            <span
              class="pointer noselect"
              @click="changeStatus(index)"
              :class="{
                'text-danger': task.status === 'Erinnerung',
                'text-success': task.status === 'Abgeschlossen',
                'text-warning': task.status === 'in Bearbeitung',
              }"
            >
              {{ capitalizeFirstChar(task.status) }}
            </span>
        </td>
        <td class="text-center">
          <div @click="deleteTask(index)">
            <span class="fa fa-trash pointer"></span>
          </div>
        </td>
        <td class="text-center">
          <div @click="editTask(index)">
            <p class="fa fa-pen pointer"></p>
          </div>
        </td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'ErinnerungenList',
  props: {
    msg: String
  },
  data () {
    return {
      task: '',
      editedTask: null,
      statuses: ['Erinnerung', 'in Bearbeitung', 'Abgeschlosssen'],
      tasks: [],
      Uhrzeit: ''
    }
  },
  methods: {
    capitalizeFirstChar (str) {
      return str.charAt(0).toUpperCase() + str.slice(1)
    },
    changeStatus (index) {
      let newIndex = this.statuses.indexOf(this.tasks[index].status)
      if (++newIndex > 2) newIndex = 0
      this.tasks[index].status = this.statuses[newIndex]
    },
    deleteTask (index) {
      this.tasks.splice(index, 1)
    },
    editTask (index) {
      this.task = this.tasks[index].name
      this.editedTask = index
    },
    submitTask () {
      if (this.task.length === 0) return
      if (this.editedTask != null) {
        this.tasks[this.editedTask].name = this.task
        this.editedTask = null
      } else {
        this.tasks.push({
          name: this.task,
          status: '-----------'
        })
      }
      this.task = ''
    }
  }
}
</script>

<style scoped>
.pointer {
  cursor: pointer;
}
.noselect {
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.line-through {
  text-decoration: line-through;
}
</style>
