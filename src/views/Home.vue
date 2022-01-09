<template>
  <div class="home">
    <div class="card h-100">
    </div>
    <img alt="Vue logo" src="../assets/erinnerungen.jpeg">
    <HelloWorld msg="Willkommen zu deinen Erinnerungen"/>
    <form class="form-signin">
      <p></p>
      <h1 class="h3 mb-3 font-weight-normal">Bitte eingeben</h1>
      <label for="inputEmail" class="sr-only">E-Mail Adresse</label>
      <p></p>
      <input type="email" id="inputEmail" class="form-control" placeholder="Email address" required="" autofocus="">
      <p></p>
      <label for="inputPassword" class="sr-only">Passwort</label>
      <p></p>
      <input type="password" id="inputPassword" class="form-control" placeholder="Password" required="">
      <div class="checkbox mb-3">
        <label>
          <input type="checkbox" value="remember-me"> Merken
        </label>
      </div>
      <button class="btn btn-lg btn-primary btn-block" type="submit">Anmelden</button>
      <p class="mt-5 mb-3 text-muted">© 2022</p>
    </form>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  }
}
</script>
