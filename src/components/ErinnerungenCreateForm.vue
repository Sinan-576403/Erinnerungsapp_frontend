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
      <form class="text-start needs-validation"  >
        <div class="mb-2">
          <label for="id" class="form-label">ID</label>
          <input type="text" class="form-control" id="id" v-model="id" >
          <div class="invalid-feedback">
            ID- Nummer
          </div>
        </div>
        <div class="mb-2">
          <label for="erste-Aufgabe" class="form-label">Erste Erinnerung</label>
          <input type="text" class="form-control" id="erste-Aufgabe" v-model="ersteAufgabe" required>
          <div class="invalid-feedback">
            Geben Sie bitte die erste Aufgabe an.
          </div>
        </div>
        <div class="mb-2">
          <label for="art" class="form-label">Art der Erinnerung</label>
          <select id="art" class="form-select" v-model="art" >
            <option value="" selected disabled>Auswählen...</option>
            <option value="Familie">Familie</option>
            <option value="Besuch">Besuch</option>
            <option value="Arbeit">Arbeit</option>
          </select>
          <div class="invalid-feedback">
            Geben Sie  bitte die wichtigere Aufgabe an.
          </div>
        </div>
        <div class="mb-2">
          <label for="nachste-Aufgabe" class="form-label">Nächste Erinnerung</label>
          <input type="text" class="form-control" id="nachste-Aufgabe" v-model="nachsteAufgabe" >
          <div class="invalid-feedback">
            Geben Sie  bitte die nächste Erinnerung an.
          </div>
        </div>
        <div class="mb-2">
          <label for="job" class="form-label">Wichtigkeit</label>
          <select id="job" class="form-select" v-model="job" >
            <option value="" selected disabled>Auswählen...</option>
            <option value="planen">Planen</option>
            <option value="sport">Sport</option>
            <option value="kochen">Kochen</option>
            <option value="termin">Termin</option>
            <option value="freizeit">Freizeit</option>
            <option value="ha">Hausaufgaben</option>
          </select>
          <div class="invalid-feedback">
            Geben Sie  bitte die wichtigere Aufgabe an.
          </div>
        </div>
        <div class="mb-2">
          <div class="form-check">
            <input class="form-check-input" type="checkbox" id="erledigt" v-model="erledigt">
            <label class="form-check-label" for="erledigt">
              erledigt
            </label>
          </div>
        </div>
        <div class="mt-5">
          <button class="btn btn-primary me-2" type="submit" @click="createErinnerung">Create</button>
          <button class="btn btn-danger me-2" type="reset">Reset</button>
          <button type="button" class="btn btn-warning " @click="deleteErinnerung">Edit</button>
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
      id: '',
      ersteAufgabe: '',
      art: '',
      nachsteAufgabe: '',
      job: '',
      erledigt: false
    }
  },
  methods: {
    createErinnerung () {
      const valid = this.validate()
      if (valid) {
        const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/api/v1/erinnerung/'

        const headers = new Headers()
        headers.append('Content-Type', 'application/json')

        const erinnerung = JSON.stringify({
          ersteAufgabe: this.ersteAufgabe,
          nachsteAufgabe: this.nachsteAufgabe,
          erledigt: this.erledigt,
          job: this.job
        })

        const requestOptions = {
          method: 'POST',
          headers: headers,
          body: erinnerung,
          redirect: 'follow'
        }
        fetch(endpoint, requestOptions)
          .catch(error => console.log('error', error))
      }
    },
    deleteErinnerung () {
      const valid = this.validate()
      if (valid) {
        const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/api/v1/erinnerung/120' + '/api/v1/erinnerung/121' + '/api/v1/erinnerung/122' + '/api/v1/erinnerung/123' + '/api/v1/erinnerung/124'

        const headers = new Headers()
        headers.append('Content-Type', 'application/json')

        const erinnerung = JSON.stringify({
          ersteAufgabe: this.ersteAufgabe,
          nachsteAufgabe: this.nachsteAufgabe,
          erledigt: this.erledigt,
          job: this.job
        })

        const requestOptions = {
          method: 'DELETE',
          headers: headers,
          body: erinnerung,
          redirect: 'follow'
        }
        fetch(endpoint, requestOptions)
          .catch(error => console.log('error', error))
      }
    },
    validate () {
      let valid = true
      // Fetch all the forms we want to apply custom Bootstrap validation styles to
      var forms = document.querySelectorAll('.needs-validation')

      // Loop over them and prevent submission
      Array.prototype.slice.call(forms)
        .forEach(function (form) {
          form.addEventListener('submit', function (event) {
            if (!form.checkValidity()) {
              valid = false
              event.preventDefault()
              event.stopPropagation()
            }

            form.classList.add('was-validated')
          }, false)
        })
      return valid
    }
  }
}
</script>

<style scoped>
body  {
  background-image: url("https://todolist.london/wp-content/uploads/2020/01/To-Do-List-Logo-for-Facebook.jpg");
  background-color: #dddddd;
}
.sticky-button {
  position: fixed;
  bottom: 20px;
  right: 20px;
  padding: 15px 15px;
  border-radius: 30px;
}
</style>
