<template>
  <h1 style="color:red;">Deine Erinnerungen</h1>
  <div class="row row-cols-1 row-cols-md-3 g-5">
    <div class="col" v-for="erinnerung in erinnerungen" :key="erinnerung.id">
      <div class="card h-100">
        <img :src="getAvatar(erinnerung)" class="card-img-top" alt="erinnerung.ersteAufgabe + ' ' + erinnerung.nachsteAufgabe">
        <div class="card-body">
          <h5 class="card-title">{{erinnerung.id}}. {{ erinnerung.ersteAufgabe }} Art:{{ erinnerung.art }} </h5>
          <p class="card-text">
            {{ erinnerung.ersteAufgabe }} ist {{ erinnerung.erledigt ? 'erledigt' : 'nicht erledigt'}} + {{ erinnerung.nachsteAufgabe}}
            muss noch {{ erinnerung.erledigt ? 'erledigt' : 'nicht erledigt'}} werden
          </p>
          <p class="card-text">
            {{ erinnerung.ersteAufgabe }} ist {{ erinnerung.erledigt ? 'erledigt' : 'nicht erledigt'}}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ErinnerungenCardList',
  props: {
    erinnerungen: {
      type: Array,
      required: true
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
