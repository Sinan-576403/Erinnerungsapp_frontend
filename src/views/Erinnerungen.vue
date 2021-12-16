<template>
  <h1>Hier sind deine Erinnerungen</h1>
  <div class="row row-cols-1 row-cols-md-3 g-4">
    <div class="col" v-for="erinnerung in erinnerungen" :key="erinnerung.id">
      <div class="card h-100">
        <img :src="getAvatar(erinnerung)" class="card-img-top" alt=" erinnerung.ersteAufgabe + ' ' + erinnerung.nachsteAufgabe">
        <div class="card-body">
          <h5 class="card-title">{{ erinnerung.ersteAufgabe }} {{ erinnerung.nachsteAufgabe}} </h5>
          <p class="card-text">
            {{ erinnerung.ersteAufgabe }} {{ erinnerung.nachsteAufgabe}} ist {{ erinnerung.erledigt ? 'erledigt' : 'nicht erledigt'}}
          </p>
          <div class="card-footer">
            <small class="text-muted">Last updated 3 mins ago</small>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Erinnerungen',
  data () {
    return {
      erinnerungen: [
        {
          id: 1,
          ersteAufgabe: 'sport',
          nachsteAufgabe: 'kochen',
          erledigt: true,
          job: 'sport'
        },
        {
          id: 2,
          ersteAufgabe: 'kochen',
          nachsteAufgabe: 'sport',
          erledigt: true,
          job: 'kochen'
        }
      ]
    }
  },
  methods: {
    getAvatar (erinnerung) {
      if (erinnerung.job === 'planen') {
        return require('../assets/planen2.jpeg')
      } else if (erinnerung.job === 'sport') {
        return require('../assets/Sport.png')
      } else if (erinnerung.job === 'kochen') {
        return require('../assets/kochen.png')
      } else if (erinnerung.job === 'termin') {
        return require('../assets/termin.png')
      } else if (erinnerung.job === 'freizeit') {
        return require('../assets/freizeit.png')
      } else if (erinnerung.job === 'ha') {
        return require('../assets/Ha.png')
      }
    }
  }
}
</script>
<style scoped>
</style>
