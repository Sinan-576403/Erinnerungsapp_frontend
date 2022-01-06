<template>
  <h1>Hier sind deine Erinnerungen</h1>
  <div class="row row-cols-1 row-cols-md-3 g-4">
    <div class="col" v-for="erinnerung in erinnerungen" :key="erinnerung.id">
      <div class="card h-100">
        <img :src="getAvatar(erinnerung)" class="card-img-top" alt="erinnerung.ersteAufgabe + ' ' + erinnerung.nachsteAufgabe">
        <div class="card-body">
          <h5 class="card-title">{{ erinnerung.ersteAufgabe }} {{ erinnerung.nachsteAufgabe}} </h5>
          <p class="card-text">
            {{ erinnerung.ersteAufgabe }} ist {{ erinnerung.erledigt ? 'erledigt' : 'nicht erledigt'}} + {{ erinnerung.nachsteAufgabe}}
            ist {{ erinnerung.erledigt ? 'erledigt' : 'nicht erledigt'}}
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
  }
}
</script>

<style scoped>
</style>
