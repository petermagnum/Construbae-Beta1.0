<template>
  <div>
    <v-app-bar app color="light-blue accent-2" dark>
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://i.imgur.com/U51aOSC.png"
          transition="scale-transition"
          width="60"
        />
      </div>

      <v-spacer />
      
      <v-btn to="/bakend-postulaciones" text>Postulaciones</v-btn>
      <v-btn to="/bakend-cotizaciones" text>Cotizaciones</v-btn>
      <v-btn to="/bakend-contacto" text>Contactos</v-btn>
      <v-btn to="/loginBakend" text>Cerrar Sesion</v-btn>
    </v-app-bar>

    <router-view />
  </div>
</template>

<script>
export default {};
</script>

<style></style>
