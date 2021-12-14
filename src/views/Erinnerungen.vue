<template>
  <h1>Hier sind deine Erinnerungen</h1>
  <div class="row row-cols-1 row-cols-md-3 g-4">
    <div class="col">
      <div class="card h-100">
        <img src="../assets/planen2.jpeg" class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title">Erste Erinnerung</h5>
          <p class="card-text">Vergiss nicht den morgigen Tag zu planen</p>
          <div class="card-footer">
            <small class="text-muted">Last updated 3 mins ago</small>
          </div>
        </div>
      </div>
    </div>
    <div class="col">
      <div class="card h-100">
        <img src="../assets/Ha.png" class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title">Zweite Erinnerung</h5>
          <p class="card-text">Vergiss nicht deine Hausaufgaben zu erledigen</p>
          <div class="card-footer">
            <small class="text-muted">Last updated 3 mins ago</small>
          </div>
        </div>
      </div>
    </div>
    <div class="col">
      <div class="card h-100">
        <img src="../assets/kochen.png" class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title">Dritte Erinnerung</h5>
          <p class="card-text">Vergiss nicht zu kochen</p>
          <div class="card-footer">
            <small class="text-muted">Last updated 3 mins ago</small>
          </div>
        </div>
      </div>
    </div>
    <div class="col">
      <div class="card h-100">
        <img src="../assets/Sport.png" class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title">Vierte Erinnerung</h5>
          <p class="card-text">Vergiss nicht Sport zu machen</p>
          <div class="card-footer">
            <small class="text-muted">Last updated 3 mins ago</small>
          </div>
        </div>
      </div>
    </div>
    <div class="col">
      <div class="card h-100">
        <img src="../assets/kochen.png" class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title">Fünfte Erinnerung</h5>
          <p class="card-text">Vergiss nicht zu kochen</p>
          <div class="card-footer">
            <small class="text-muted">Last updated 3 mins ago</small>
          </div>
        </div>
      </div>
    </div><div class="col">
    <div class="card h-100">
      <img src="../assets/kochen.png" class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">Sechste Erinnerung</h5>
        <p class="card-text">Vergiss nicht zu kochen</p>
        <div class="card-footer">
          <small class="text-muted">Last updated 3 mins ago</small>
        </div>
      </div>
    </div>
  </div>
    <div class="col">
      <div class="card h-100">
        <img src="../assets/Ha.png" class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title">Siebte Erinnerung</h5>
          <p class="card-text">Vergiss nicht deine Hausaufgaben zu erledigen</p>
          <div class="card-footer">
            <small class="text-muted">Last updated 3 mins ago</small>
          </div>
        </div>
      </div>
    </div>
  </div>
  <table class="table table-hover">
    <thead>
    <tr>
      <th scope="col"></th>
      <th scope="col">ERSTE ERINNERUNG</th>
      <th scope="col">LETZTE ERINNERUNG</th>
      <th scope="col">ERLEDIGT?</th>
    </tr>
    </thead>
    <tbody>
    <tr>
      <th scope="row">1) 12.12.2021</th>
      <td>SPORT</td>
      <td>KOCHEN</td>
      <td>JA</td>
    </tr>
    <tr>
      <th scope="row">2) 13.12.2021</th>
      <td>PLANEN</td>
      <td>HA</td>
      <td>NEIN</td>
    </tr>
    <tr>
      <th scope="row">3) 13.12.2021</th>
      <td>SPORT</td>
      <td>KOCHEN</td>
      <td>JA</td>
    </tr> <tr>
      <th scope="row">4) 14.12.2021</th>
      <td>SPORT</td>
      <td>KOCHEN</td>
      <td>JA</td>
    </tr> <tr>
      <th scope="row">5) 15.12.2021</th>
      <td>SPORT</td>
      <td>KOCHEN</td>
      <td>JA</td>
    </tr> <tr>
      <th scope="row">6) 16.12.2021</th>
      <td>SPORT</td>
      <td>KOCHEN</td>
      <td>JA</td>
    </tr> <tr>
      <th scope="row">7) 17.12.2021</th>
      <td>SPORT</td>
      <td>KOCHEN</td>
      <td>JA</td>
    </tr>
    </tbody>
  </table>
</template>
<script>
export default {
  name: 'Erinnerungen'
}
</script>
<style scoped>
</style>
