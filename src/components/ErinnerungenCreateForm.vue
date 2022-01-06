<template>
  <button class="btn btn-success sticky-button" data-bs-toggle="offcanvas" data-bs-target="#erinnerungen-create-offcanvas" aria-controls="#erinnerungen-create-offcanvas">
    <i class="bi bi-erinnerungen-plus-fill"></i>
  </button>
  <div class="offcanvas offcanvas-end" tabindex="-1" id="erinnerungen-create-offcanvas" aria-labelledby="offcanvas-label">
    <div class="offcanvas-header">
      <h5 id="offcanvas-label">Neue Erinnerung</h5>
      <button type="button" id="close-offcanvas" class="btn-close text-reset" data-bs-dismiss="offcanvas" aria-label="Close"></button>
    </div>
    <div class="offcanvas-body">
      <form class="text-start needs-validation" id="erinnerungen-create-form" novalidate>
        <div class="mb-3">
          <label for="erste-Aufgabe" class="form-label">Erste Aufgabe</label>
          <input type="text" class="form-control" id="erste-Aufgabe" v-model="ersteAufgabe">
          <div class="invalid-feedback">
            Please provide the erste Aufgabe.
          </div>
        </div>
        <div class="mb-3">
          <label for="nachste-Aufgabe" class="form-label">Nächste Aufgabe</label>
          <input type="text" class="form-control" id="nachste-Aufgabe" v-model="nachsteAufgabe">
          <div class="invalid-feedback">
            Please provide the nachste Aufgabe.
          </div>
        </div>
        <div class="mb-3">
          <label for="job" class="form-label">Wichtigkeit</label>
          <select id="job" class="form-select" v-model="job">
            <option value="" selected disabled>Auswählen...</option>
            <option value="planen">planen</option>
            <option value="sport">sport</option>
            <option value="kochen">kochen</option>
            <option value="termin">termin</option>
            <option value="freizeit">freizeit</option>
            <option value="ha">ha</option>
          </select>
          <div class="invalid-feedback">
            Please select a valid job.
          </div>
        </div>
        <div class="mb-3">
          <div class="form-check">
            <input class="form-check-input" type="checkbox" id="erledigt" v-model="erledigt">
            <label class="form-check-label" for="erledigt">
              erledigt
            </label>
          </div>
        </div>
        <div class="mt-5">
          <button class="btn btn-primary me-3" type="submit" @click.prevent="createErinnerung">Create</button>
          <button class="btn btn-danger" type="reset">Reset</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ErinnerungenCreateForm',
  data () {
    return {
      ersteAufgabe: '',
      nachsteAufgabe: '',
      job: '',
      erledigt: false
    }
  },
  methods: {
    createErinnerung () {
      console.log(this.ersteAufgabe)
      console.log(this.nachsteAufgabe)
      console.log(this.job)
      console.log(this.erledigt)
    }
  }
}

</script>

<style scoped>
.sticky-button {
  position: fixed;
  bottom: 20px;
  right: 20px;
  padding: 10px 20px;
  border-radius: 30px;
}
</style>
