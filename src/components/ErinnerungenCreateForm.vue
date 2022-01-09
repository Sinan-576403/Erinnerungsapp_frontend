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
      <form class="text-start needs-validation" novalidate >
        <div class="mb-3">
          <label for="erste-Aufgabe" class="form-label">Erste Aufgabe</label>
          <input type="text" class="form-control" id="erste-Aufgabe" v-model="ersteAufgabe" required>
          <div class="invalid-feedback">
            Geben Sie bitte die erste Aufgabe an.
          </div>
          </div>
        <div class="mb-3">
          <label for="nachste-Aufgabe" class="form-label">Nächste Aufgabe</label>
          <input type="text" class="form-control" id="nachste-Aufgabe" v-model="nachsteAufgabe" required>
          <div class="invalid-feedback">
            Geben Sie  bitte die nächste Aufgabe an.
          </div>
          </div>
        <div class="mb-3">
          <label for="job" class="form-label">Wichtigkeit</label>
          <select id="job" class="form-select" v-model="job" required>
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
        <div class="mb-3">
          <div class="form-check">
            <input class="form-check-input" type="checkbox" id="erledigt" v-model="erledigt">
            <label class="form-check-label" for="erledigt">
              erledigt
            </label>
          </div>
        </div>
        <div class="mt-5">
          <button class="btn btn-primary me-3" type="submit" @click="createErinnerung">Create</button>
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
      const valid = this.validate()
      if (valid) {
        const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/api/v1/erinnerung'

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
.sticky-button {
  position: fixed;
  bottom: 20px;
  right: 20px;
  padding: 10px 20px;
  border-radius: 30px;
}
</style>
