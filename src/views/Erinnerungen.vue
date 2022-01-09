<template>
  <h1></h1>
  <div class="container-fluid">
    <erinnerungen-card-list :erinnerungen="this.erinnerungen"></erinnerungen-card-list>
  </div>
  <erinnerungen-create-form></erinnerungen-create-form>
</template>

<script>
import ErinnerungenCardList from '@/components/ErinnerungenCardList'
import ErinnerungenCreateForm from '@/components/ErinnerungenCreateForm'

export default {
  name: 'Erinnerungen',
  components: {
    ErinnerungenCardList,
    ErinnerungenCreateForm
  },
  data () {
    return {
      erinnerungen: []
    }
  },
  mounted () {
    const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/api/v1/erinnerung'
    const requestOptions = {
      method: 'GET',
      redirect: 'follow'
    }
    fetch(endpoint, requestOptions)
      .then(response => response.json())
      .then(result => result.forEach(erinnerung => {
        this.erinnerungen.push(erinnerung)
      }))
      .catch(error => console.log('error', error))
  }
}
</script>
<style scoped>
</style>
